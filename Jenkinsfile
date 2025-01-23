node {
    // Menjalankan Docker container dengan image Maven yang sudah terinstal
    docker.image('maven:3.9-eclipse-temurin-8-alpine').withRun('-p 3000:3000') { dockerContainer ->
        
        stage('Build') {
            // Menjalankan perintah Maven untuk build project
            sh 'mvn clean install'
        }
    }
}