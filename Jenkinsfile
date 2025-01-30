node {
    // Mendapatkan Docker image dan menjalankan perintah di dalamnya
    docker.image('maven:3.9.9-eclipse-temurin-17-alpine-1').inside('-v agent-data:/var/agent_home') {
        
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
            sshagent (credentials: [ 'aws-key' ]) {
                sh 'scp -o StrictHostKeyChecking=no . ec2-user@18.141.145.145:/apps'
                // sh 'ssh -o StrictHostKeyChecking=no ec2-user@18.141.145.145 "cd /apps && ./deliver.sh"'
                // sh 'scp -o StrictHostKeyChecking=no ./target/my-app-1.0-SNAPSHOT.jar ec2-user@18.141.145.145:/apps'
                // sh 'ssh -o StrictHostKeyChecking=no ec2-user@18.141.145.145 "java -jar /apps/target/my-app-1.0-SNAPSHOT.jar"'
            }

            sleep time: 1, unit: 'MINUTES'
        }
    }
}
