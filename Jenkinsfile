node {
    // Menjalankan Docker container dengan image yang telah dibuat sebelumnya
    docker.image('maven:3.8.7-openjdk-18-slim').inside('-p 3000:3000') {
        
        stage('Build') {
            // Menjalankan perintah Maven untuk build project
            sh 'mvn -B -DskipTests clean package'
        }
    }
}