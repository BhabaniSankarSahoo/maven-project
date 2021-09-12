pipeline{
    agent any
    stages{
        stage(" scm checkout "){
            steps{
                echo "-----downloading code from scm-----"
                git branch: 'master', url: 'https://github.com/BhabaniSankarSahoo/maven-project.git'
            }
        }
        stage(" build the artifact "){
            steps{
                echo "-----build the artifact-----"
                withMaven(jdk: 'local_jdk', maven: 'local_maven') {
                 sh 'mvn clean package'                                   // mvn goal
                }
            }
        }
    }
}
