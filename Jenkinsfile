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
                    sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=DevSecOpsApp -Dsonar.token=sqp_60047f7badcb803bc87bd8c615ac50a605047c76 -Dsonar.host.url=http://localhost:9000'
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
