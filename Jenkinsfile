pipeline {
    agent any

    tools {
        maven 'Maven_3.9.9'
        jdk 'JDK_24'
    }

    environment {
        JAVA_HOME = 'C:/Program Files/Java/jdk-24'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
        SONARQUBE = 'LocalSonarQube'
        SONAR_TOKEN = credentials('sonar-token')
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/HARIRAM19/DevSecOpsApp'
            }
        }

        stages {
        stage('Check Java') {
            steps {
                sh 'echo $JAVA_HOME'
                sh 'java -version'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv("${SONARQUBE}") {
                    sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=DevSecOpsApp -Dsonar.token=sqp_60047f7badcb803bc87bd8c615ac50a605047c76 -Dsonar.host.url=http://10.10.53.100:9000'
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
