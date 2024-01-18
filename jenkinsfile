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
             sh 'ssh root@172.31.2.55'
             sh 'scp /home/slave01/workspace/SamplePipeline/target/Parcel-service root@172.31.2.55:/opt/apache-tomcat-8.5.98/webapps/'
            }
        }
    }
}
