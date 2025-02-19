pipeline {
    agent any

    tools {
      jdk 'JDK'
      maven 'MAVEN3'
    }

    stages {
        stage('Checkout'){
            steps {
                git branch: 'main', url: 'https://github.com/Dom1232/Quiz3.git'
            }
        }
        stage('Build'){
            steps {
                bat "mvn clean package -DskipTests"
            }
        }
        stage('Run Tests with Jacoco') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Generate Coverage'){
            steps {
                sh 'mvn jacoco:report'
            }
        }
        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}