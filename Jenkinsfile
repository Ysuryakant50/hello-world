pipeline {
    agent any
    environment {
        MAVEN_HOME = '/usr/share/maven' // Path to Maven installation
    }
    tools {
        maven 'Maven 3.6.3' // Replace with your Maven tool name configured in Jenkins
    }
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Ysuryakant50/hello-world.git'
            }
        }
        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Run Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Code Analysis with SonarQube') {
            environment {
                SONARQUBE_SERVER = 'SonarQubeServer' // Replace with your SonarQube installation name
            }
            steps {
                withSonarQubeEnv(SONARQUBE_SERVER) {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
