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
                sh 'ls'
                sh 'which gradle"
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
                sh '. ./startDatabase.sh'
                sh './gradlew bootRun'
            }
        }
        stage('Deliver') { 
            steps {
                echo 'Delivering' 
            }
        }
    }
}
