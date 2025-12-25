pipeline {
    agent any

    stages {

        stage('Run URL Availability Test') {
            steps {
                sh 'java -version'
                sh 'mvn -version'
                sh 'mvn clean test'
                junit 'target/surefire-reports/*.xml'
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploy OK'
            }
        }
    }
}
