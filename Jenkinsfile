pipeline {
    agent {
        docker {
            image 'maven:3.8.4-jdk-11' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
}