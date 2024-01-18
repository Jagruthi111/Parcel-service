pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'maven'
        SPRING_PROFILES_ACTIVE = 'local'  // Set the Spring profile for local development
    }

    stages {
        stage('Checkout') {
            steps {
                sh 'rm -rf Parcel-service'
            sh 'git clone https://github.com/Jagruthi111/Parcel-service/'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the Spring Boot application
                    sh "${MAVEN_HOME}/bin/mvn clean package"
                }
            }
        }

        stage('Run Locally') {
            steps {
                script {
                    // Run the Spring Boot application locally
                    sh "java -jar target/simple-parcel-service-app-1.0-SNAPSHOT.jar --spring.profiles.active=${SPRING_PROFILES_ACTIVE} &"

                    // Sleep for a while to allow the application to start (adjust as needed)
                    sleep time: 30, unit: 'SECONDS'
                }
            }
        }
}




