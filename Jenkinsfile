node {
    docker.image('gradle:alpine').inside('-v /root/.gradle:/root/.gradle') {
        stage('Build') { 
            echo 'Building' 
            sh 'ls'
            sh 'which gradle'
        }
        stage('Test') {            
            echo 'Testing'
            sh './gradlew bootRun'            
        }
        stage('Deliver') { 
            echo 'Delivering' 
        }
    }
}
