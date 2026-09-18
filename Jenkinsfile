pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Git repository එකෙන් ඔබගේ අලුත්ම කෝඩ් එක ගන්නවා
                checkout scm
            }
        }

        stage('Build Docker Images') {
            steps {
                echo 'Building Frontend and Backend Images...'
                // docker-compose.yml එකට අනුව images දෙකම අලුතින් build කරනවා
                bat 'docker-compose build'
            }
        }

        stage('Deploy Containers') {
            steps {
                echo 'Starting Containers...'
                // Containers ටික background එකේ (-d) run කරනවා
                bat 'docker-compose up -d'
            }
        }
    }
}