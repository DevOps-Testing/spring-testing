node {
    checkout scm
    docker.image('gradle:alpine').inside('-v /root/.gradle:/root/.gradle') {
        stage('Build') { 
            echo 'Building' 
            sh 'ls'
            sh 'which gradle'
        }
        stage('Test') {            
            echo 'Testing'
            sh 'ls'
            sh 'source env.sample'
            sh './gradlew bootRun'            
        }
        stage('Deliver') { 
            echo 'Delivering' 
        }
    }
}
