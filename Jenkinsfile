node {
    // Menjalankan Docker container dengan image yang telah dibuat sebelumnya
    docker.image('maven:3.9-eclipse-temurin-8-alpine').inside('-p 3000:3000') {
        
        stage('Build') {
            // Menjalankan perintah Maven untuk build project
            sh 'mvn install clean'
        }
    }
}