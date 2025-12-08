pipeline {
    agent any

    environment {
        MAVEN_OPTS = "-Dmaven.test.skip=true"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/MohammadMana1/spring-mysql-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean install -DskipTests'
            }
        }

        // Publish to Nexus is optional for your homework.
        // You REMOVE IT to avoid build failures.
        //
        // stage('Publish to Nexus') {
        //     steps {
        //         sh "./mvnw deploy"
        //     }
        // }

    }
}
