pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                // Use the Maven Wrapper so Jenkins does not need Maven preinstalled
                sh './mvnw clean package -DskipTests'
            }
        }
        stage('Publish to Nexus') {
            steps {
                // This will run "mvn deploy" using your pom.xml config
                sh './mvnw deploy -DskipTests'
            }
        }
    }
}
