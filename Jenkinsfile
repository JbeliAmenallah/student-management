pipeline {
    agent any

    tools {
        maven 'Maven3'     
        jdk 'JDK17'        
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                sh 'mvn clean verify'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package -DskipTests'
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }

        success {
            echo 'Build réussi ✅'
        }

        failure {
            echo 'Build échoué ❌'
        }
    }
}
