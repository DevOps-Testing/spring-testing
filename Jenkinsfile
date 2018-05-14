node {
    checkout scm    
    docker.image('postgres').withRun('-p 15432:5432 -e "POSTGRES_PASSWORD=password" -e "POSTGRES_USER=testuser"') { c ->
        docker.image('postgres').inside("--link ${c.id}:db") {
            /* Wait until mysql service is up */
            sh 'hostname && pwd && ls'
            sh 'apk --update iputils'
            sh 'while ! pg_isready -h "db" -p "15432"; do sleep 10; done'
        }
        docker.image('gradle:alpine').inside("--link ${c.id}:db -v /root/.gradle:/root/.gradle") {
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
}
