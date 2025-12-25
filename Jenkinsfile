pipeline {
    agent {
        docker {
            image 'maven:3.9.9-eclipse-temurin-21'
            args '-v /root/.m2:/root/.m2'
        }
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run URL Availability Test') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
                sh 'mvn clean test'
                junit 'target/surefire-reports/*.xml'
            }
        }

        stage('Deploy') {
            when {
                expression { currentBuild.currentResult == 'SUCCESS' }
            }
            steps {
                echo '🚀 Deploy aşaması çalışıyor'
            }
        }
    }
}
