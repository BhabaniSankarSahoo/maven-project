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
            sshagent(['tomcat-user']) {
                sh 'scp -o StrictHostKeyChecking=no */target/*.war tomcat-user@192.168.56.102:/var/lib/tomcat/webapps' // some block
            }
        }
    }
}
post{
    always{
        mail bcc: '', body: 'dddd', cc: '', from: '', replyTo: 'dcs', subject: 'abc', to: 'bhabani.sankar.sahoo@hotmail.com'
    }
}

}
