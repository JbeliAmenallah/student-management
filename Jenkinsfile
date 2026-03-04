pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
        stage('SONARQUBE Analysis') {
            steps {
                withCredentials([string(credentialsId: 'sonarqube', variable: 'SONAR_TOKEN')]) {
                    sh "mvn sonar:sonar -Dsonar.projectKey=devops_git -Dsonar.host.url=${SONAR_HOST_URL} -Dsonar.token=${SONAR_TOKEN}"
                }
            }
        }
    }
}
