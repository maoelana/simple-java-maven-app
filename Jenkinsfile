node {
    // Mendapatkan Docker image dan menjalankan perintah di dalamnya
    docker.image('maven:3.9.9-eclipse-temurin-17-alpine').inside() {
        
        stage('Checkout') {
            // Melakukan checkout kode dari repository Git
            checkout scm
        }

        stage('Build') {
            // Menjalankan Maven untuk mem-build project tanpa menjalankan test
            sh 'mvn -B -DskipTests clean package'
        }

        stage('Test') {
            // Menjalankan test dengan Maven
            sh 'mvn test'
        }

        stage('Manual Approval') {
            input 'Lanjutkan ke tahap Deploy?'
        }

        stage('Deploy') {
            sh './jenkins/scripts/deliver.sh'
            
            withCredentials([sshUserPrivateKey(credentialsId: 'ec2-access', keyFileVariable: 'SSH_KEY')]) {
                sh 'scp -o StrictHostKeyChecking=no -i "$SSH_KEY" target/my-app-1.0-SNAPSHOT.jar ec2-user@54.179.37.98:/apps'
            }

            sleep time: 1, unit: 'MINUTES'
        }
    }
}
