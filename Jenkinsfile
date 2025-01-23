node {
    // Install maven
    docker.image('maven:3.9.9-eclipse-temurin-17-alpine').inside('-p 3000:3000') {
        stage('Checkout') {
            checkout scm
        }
        stage('Build') {
            // Perintah Maven untuk build project
            sh 'mvn -B -DskipTests clean package'
        }

        stage('Test') {
            // Perintah Maven untuk test project
            sh 'mvn test'
        }
    }
}