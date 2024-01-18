pipeline { label 'slave01'}

environment {
    MAVEN_HOME = tool 'Maven'
}

stages {
    stage('Checkout') {
        steps {
            sh 'rm -rf Parcel-service'
            sh 'git clone https://github.com/Jagruthi111/Parcel-service/'
        }
    }

    stage('Build') {
        steps {
            script {
                sh "${MAVEN_HOME}/bin/mvn clean package"
            }
        }
    }

    stage('Run Locally') {
        steps {
            script {
                // Run the Spring Boot application locally
                sh "java -jar target/simple-parcel-service-app-1.0-SNAPSHOT.jar &"
                
                // Sleep for a while to allow the application to start (adjust as needed)
                sleep 30
            }
        }
    }

    stage('Deploy to Tomcat') {
        steps {
            script {
                // Copy the JAR file to the Tomcat webapps directory
                sh 'ssh root@172.31.2.55'
                sh 'scp target/simple-parcel-service-app-1.0-SNAPSHOT.jar root@172.31.2.55:/opt/apache-tomcat-8.5.98/webapps/'

                // Restart Tomcat
                sh "/opt/apache-tomcat-8.5.98/bin/shutdown.sh"
                sh "/opt/apache-tomcat-8.5.98/bin/startup.sh"
            }
        }
    }
}
