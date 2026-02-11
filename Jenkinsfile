pipeline {
    agent any

  environment {
        JAVA_HOME = "/usr/lib/jvm/java-21-openjdk-amd64"
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    tools {
        maven 'Maven3'
    }
 
    stages {
        stage('Compile & Test') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }
    }
}
