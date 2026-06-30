pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                echo 'Fetching project files'
            }
        }

        stage('Build Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t maven1 .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8080:8080 --name javaapp maven1'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}
