pipeline {
    agent any

    environment {
        NEXUS_URL = "http://nexus-service.final-k8s.svc.cluster.local:8081"
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
                sh "./mvnw deploy -DskipTests -Dnexus.url=${NEXUS_URL}"
            }
        }

        stage('Verify Artifact') {
            steps {
                sh "curl -I ${NEXUS_URL}/repository/maven-snapshots/"
            }
        }
    }
}
