node {
    // Menjalankan Docker container dengan image Maven yang sudah terinstal
    docker.image('maven:3-eclipse-temurin-8-alpine').inside('-p 3000:3000') { dockerContainer ->
        
        stage('Build') {
            // Menjalankan perintah Maven untuk build project
            sh 'mvn install clean'
        }
    }
}