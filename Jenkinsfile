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
                sh 'chmod u+x /home/slave01/workspace/SamplePipeline/target/hello-world-war-1.0.0.war'
                sh 'java -jar "target/simple-parcel-service-app-1.0-SNAPSHOT.jar"'
                sh 'sleep 30s'
            }
        }
 stage('deploy') {
            steps { 
             sh 'ssh root@172.31.2.55'
             sh 'scp /home/slave01/workspace/SamplePipeline/target/hello-world-war-1.0.0.war root@172.31.2.55:/opt/apache-tomcat-8.5.98/webapps/'

            }
        }
    }
}
