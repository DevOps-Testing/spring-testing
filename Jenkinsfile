node {
    checkout scm    
    docker.image('postgres').withRun('-p 15432:5432 -e "POSTGRES_PASSWORD=password" -e "POSTGRES_USER=testuser"').inside('') {
        
        /* Wait until postgres service is up */
        sh 'hostname && pwd && ls && id'
        sh 'while ! pg_isready; do sleep 10; done'
    }
}
