pipeline {
    agent { label 'slave01'}
    stages {
        stage('checkout') {
            steps {
                sh 'rm -rf Parcel-service'
                sh 'git clone -b feature-1 https://github.com/Jagruthi111/Parcel-service/'
            }
        }
        stage('build') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean install'
                chmod u+x simple-parcel-service-app-1.0-SNAPSHOT.jar
                ./simple-parcel-service-app-1.0-SNAPSHOT.jar
                sleep 30
            }
        }
 stage('deploy') {
            steps { 
             sh 'java -jar /home/slave01/workspace/Parcelpipeline/target/simple-parcel-service-app-1.0-SNAPSHOT.jar'
            }
        }
    }
}
