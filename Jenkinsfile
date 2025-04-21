pipeline {
    agent any

    tools {
        maven 'Maven'
        jdk 'Java-24'
    }

    environment {
        SONARQUBE = 'LocalSonarQube'
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/HARIRAM19/DevSecOpsApp'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE}") {
                    sh 'mvn clean verify sonar:sonar'
                }
            }
        }

        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
    }
}
