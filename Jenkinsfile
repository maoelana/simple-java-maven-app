pipeline {
    agent {
        docker {
            image 'maven:3.8.6-openjdk-8-slim' 
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