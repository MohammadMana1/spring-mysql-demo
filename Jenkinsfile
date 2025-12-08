pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/MohammadMana1/spring-mysql-demo.git'
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
                sh "curl -I http://10.100.251.249:8081/repository/maven-snapshots/"
            }
        }
    }
}
