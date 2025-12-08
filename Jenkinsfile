pipeline {
    agent any

    environment {
        // Internal Nexus DNS inside Kubernetes
        NEXUS_URL = "http://nexus-service.final-k8s.svc.cluster.local:8081"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Publish to Nexus') {
            steps {
                sh """
                    ./mvnw deploy -DskipTests \
                    -Dnexus.url=${NEXUS_URL}
                """
            }
        }

        stage('Verify Artifact') {
            steps {
                sh "ls -l target/"
                echo "Artifact deployed to Nexus at ${NEXUS_URL}"
            }
        }
    }
}
