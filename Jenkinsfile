pipeline {
    agent {
        docker {
            image 'maven:3.5-jdk-8-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                echo 'Building' 
                sh 'ls'
                sh 'which mvn'
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test') {
            steps {
                //sh 'export WEATHER_API_KEY=3a05ecd95518992366b3d7ca5a853d74; ./gradlew bootRun'  
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') { 
            steps {
                echo 'insert delivery scripts here'
                //sh './jenkins/scripts/deliver.sh' 
            }
        }
    }
}
