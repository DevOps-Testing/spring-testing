node {
    docker.image('gradle:alpine').inside('-v /root/.gradle:/root/.gradle') {
        stage('Build') { 
            steps {
                echo 'Building' 
                sh 'ls'
                sh 'which gradle'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
                sh './gradlew bootRun'
            }
        }
        stage('Deliver') { 
            steps {
                echo 'Delivering' 
                sh '. ./startDatabase.sh'
            }
        }
    }
}
