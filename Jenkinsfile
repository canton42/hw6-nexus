pipeline {
    agent any

    tools {
        maven '3.9.11'
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/canton42/hw6-nexus.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Upload to Nexus') {
            steps {
                sh '''
                curl -v -u admin:easy123456 \
                --upload-file target/*.jar \
                http://host.docker.internal:8081/repository/maven-releases/com/example/app/1.0/app-1.0.jar
                '''
            }
        }
    }
}
