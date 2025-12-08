pipeline {
    agent any
    
    stages {

        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }

        stage('Checkout') {
            steps {
                sh 'git checkout main'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean install -DskipTests'
            }
        }

        stage('Publish to Nexus') {
            steps {
                echo "Simulating Nexus upload for assignment requirements"
            }
        }
    }
}
