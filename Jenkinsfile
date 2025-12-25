pipeline {
    agent any

    tools {
        jdk 'JDK21'
        maven 'Maven3'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Run URL Availability Test') {
            steps {
                sh 'mvn clean test'
                junit 'target/surefire-reports/*.xml'
            }
        }

        stage('Deploy') {
            when {
                expression {
                    currentBuild.currentResult == 'SUCCESS'
                }
            }
            steps {
                echo '🚀 Deploy aşaması çalışıyor'
                sh 'echo "DEPLOY OK"'
            }
        }
    }

    post {
        failure {
            echo '❌ URL erişilemedi, pipeline fail oldu'
        }
        success {
            echo '✅ URL erişilebilir, deploy başarılı'
        }
    }
}
