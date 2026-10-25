
pipeline {
    agent any

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Build successful'
                bat 'docker build -t vipul .'
            }
        }

        stage('Test') {
            steps {
                echo 'Test successful'
            }
        }

        stage('Deploy') {
            steps {
                bat 'docker stop vipulcon || exit 0'
                bat 'docker rm vipulcon || exit 0'
                bat 'docker run -d --name vipulcon -p 8081:80 vipul'
            }
        }
    }
}
