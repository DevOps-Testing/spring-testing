pipeline {
    agent {
        docker {
            image 'gradle:alpine' 
            args '-v /root/.gradle:/root/.gradle' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                echo 'Building' 
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
                sh './startDatabase'
                sh './gradlew bootRun'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') { 
            steps {
                echo 'Delivering' 
            }
        }
    }
}
