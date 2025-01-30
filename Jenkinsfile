node {
    // Mendapatkan Docker image dan menjalankan perintah di dalamnya
    docker.image('maven:3.9.9-eclipse-temurin-17-alpine').inside(" -v /etc/passwd:/etc/passwd -v /var/lib/jenkins/.ssh/:/var/lib/jenkins/.ssh/ ") {
        
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
            // withCredentials([sshUserPrivateKey(credentialsId: 'aws-key', keyFileVariable: 'AWS_KEY')]) {
            //     sh 'ssh ec2-user@18.141.145.145'
            // }
            sshagent (credentials: [ 'aws-key' ]) {
                sh "ssh -vvv -o StrictHostKeyChecking=no ec2-user@18.141.145.145 uname -a"
            }

            sleep time: 1, unit: 'MINUTES'
        }
    }
}
