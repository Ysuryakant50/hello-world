pipeline {

    agent any



    environment {

        MAVEN_HOME = '/usr/share/maven' // Path to Maven installation


    }



    stages {

        stage('Checkout Code') { // Clones the repository

            steps {

                git 'https://github.com/Ysuryakant50/hello-world.git'

            }

        }



        stage('Build with Maven') { // Builds the project and creates JAR/WAR

            steps {

                sh 'mvn clean package'

            }

        }



        stage('Run Unit Tests') { // Executes unit tests

            steps {

                sh 'mvn test'

            }

        }

        stage('Code Analysis with SonarQube') { // Runs static code analysis

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
