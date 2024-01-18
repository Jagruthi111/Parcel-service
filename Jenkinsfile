pipeline {
    agent { label 'slave01'}
    stages {
        stage('checkout') {
            steps {
                sh 'rm -rf Parcel-service'
                sh 'git clone https://github.com/Jagruthi111/Parcel-service/'
            }
        }
        stage('build') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean install'
            }
        }
 stage('deploy') {
            steps { 
             sh 'java -jar "/home/slave01/workspace/Pacelpipeline/target/simple-parcel-service-app-1.0-SNAPSHOT.jar"'
            }
        }
    }
}
