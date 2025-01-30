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
            withCredentials([sshUserPrivateKey(credentialsId: 'ec2-access', keyFileVariable: 'SSH_KEY')]) {
                sh 'ssh -o StrictHostKeyChecking=no -i "$SSH_KEY" ec2-user@18.141.145.145 "./jenkins/scripts/deliver.sh"'
                sh 'scp -o StrictHostKeyChecking=no -i "$SSH_KEY" target/my-app-1.0-SNAPSHOT.jar ec2-user@18.141.145.145:/apps'
            }

            sleep time: 1, unit: 'MINUTES'
        }
    }
}
