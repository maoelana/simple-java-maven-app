pipeline {
    agent {
        docker {
            image 'maven:3.8.7-openjdk-18-slim' 
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