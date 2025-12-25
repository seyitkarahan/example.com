pipeline {
    agent any

    tools {
        maven 'Maven'
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
            }
        }

        stage('Deploy') {
            when {
                expression {
                    currentBuild.currentResult == 'SUCCESS'
                }
            }
            steps {
                echo 'Deploy aşaması çalışıyor...'
                sh 'echo "DEPLOY OK"'  // şimdilik dummy
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
