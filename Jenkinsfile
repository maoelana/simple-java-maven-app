node {
    // Install maven
    docker.image('maven:3.9.9-eclipse-temurin-17-alpine') {

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
            // Perintah Maven untuk build project
            sh 'mvn -B -DskipTests clean package'
        }

        stage('Test') {
            // Perintah Maven untuk test project
            sh 'mvn test'
        }
    }
}