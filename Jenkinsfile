node {
    checkout scm
    docker.image('gradle:alpine').inside('-v /root/.gradle:/root/.gradle -p 30085:8080 -p 30089:8089') {
        stage('Build') { 
            echo 'Building' 
            sh 'ls'
            sh 'which gradle'
        }
        stage('Test') {            
            echo 'Testing'
            sh 'export WEATHER_API_KEY=3a05ecd95518992366b3d7ca5a853d74; ./gradlew bootRun'            
        }
        stage('Deliver') { 
            echo 'Delivering' 
        }
    }
}
