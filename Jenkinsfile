pipeline {
    agent any 
    tools{
        maven 'my_maven'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Archive') {
            steps {
                sh 'curl -v -u admin:admin123 --upload-file web/target/*.war http://localhost:8081/nexus/content/repositories/Repo123/'
            }
        }
    }
}
