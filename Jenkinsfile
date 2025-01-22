pipeline {
    agent {
        docker {
            image 'maven:3.9.2-openjdk-17'
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