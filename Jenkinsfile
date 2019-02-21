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
                sh 'curl -v -u admin:admin123 --upload-file /var/jenkins_home/workspace/jenkinsfile-git-maven/target/*.jar http://http://54.235.47.80:8081/nexus/content/repositories/Repo123/'
            }
        }
    }
}
