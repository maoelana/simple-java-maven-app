node {
    // Install maven
    docker.image('maven:3.9.9-eclipse-temurin-17-alpine').inside('-p 3000:3000') {

        stage('Checkout') {
            checkout scmGit(
                branches: 
                    [[name: '*/master']], 
                    extensions: [], 
                    userRemoteConfigs: 
                    [[url: '/home/Code/belajar-jenkins/simple-java-maven-app']]
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