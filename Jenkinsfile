pipeline {
    agent any

    environment {
        NEXUS_URL = "http://192.168.49.2:30081"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/MohammadMana1/spring-mysql-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh "./mvnw clean package -DskipTests"
            }
        }

        stage('Publish to Nexus') {
            steps {
                sh "./mvnw deploy -DskipTests"
            }
        }

        stage('Verify Artifact') {
            steps {
                sh "curl -I ${NEXUS_URL}/repository/maven-snapshots/"
            }
        }
    }
}
