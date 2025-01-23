node {
    // Mendapatkan Docker image dan menjalankan perintah di dalamnya
    docker.image('maven:3.9.9-eclipse-temurin-17-alpine').inside() {
        
        stage('Checkout') {
            checkout scmGit(
                branches: 
                    [[name: '*/master']], 
                    extensions: [], 
                    userRemoteConfigs: 
                    [[url: 'https://github.com/maoelana/simple-java-maven-app.git']]
            )
        }
        
        stage('Build') {
            // Menjalankan Maven untuk mem-build project tanpa menjalankan test
            sh 'mvn -B -DskipTests clean package'
        }

        stage('Test') {
            // Menjalankan test dengan Maven
            sh 'mvn test'
        }
    }

}
