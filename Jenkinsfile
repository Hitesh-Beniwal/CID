pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    echo 'Cloning repository from GitHub...'
                    git 'https://github.com/Hitesh-Beniwal/CID.git'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    echo 'Building the application...'
                    bat 'mvn clean package'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Running unit tests...'
                    bat 'mvn test'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying application...'
                    bat 'scp target/*.jar user@server:/opt/app/'
                }
            }
        }
    }

    post {
        always {
            script {
                echo 'Pipeline execution complete'
            }
        }

        failure {
            mail to: 'hitesh0001beniwal@gmail.com',
                 subject: 'Jenkins Build Failed',
                 body: 'The Jenkins pipeline has failed. Check Jenkins logs for details.'
        }
    }
}
