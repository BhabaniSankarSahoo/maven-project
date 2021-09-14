pipeline{
    // agent declartion 
    agent any
stages{
    stage('SCM checkout'){
        steps{
            git branch: 'master', url: 'https://github.com/BhabaniSankarSahoo/maven-project.git'
        }
    }

    stage('code build'){
        steps{
            withMaven(jdk: 'local_jdk', maven: 'local_maven') {
                sh 'mvn clean package'                              // some block
            }
        }
    }

    stage('archive the arifacts'){
        steps{
            archiveArtifacts artifacts: '**/*.war', followSymlinks: false
        }
    }

    stage('copy/deploy artifacts to server'){
        steps{
            sshagent(['ec2-user']) {
                sh 'scp -o StrictHostKeyChecking=no **/*.war ec2-user@13.126.172.48:/var/lib/tomcat/webapps' // some block
            }
        }
    }



}
}
