pipeline {
    agent any
    stages {
        stage('Clonage du dépôt GitHub') {
            steps {
                git branch: 'main', url: 'https://github.com/CharlyRousseau/OSDetector.git'
            }
        }
        stage('Installation de Python 3.11 et pip') {
            steps {
                sh '''
                    sudo apt update
                    sudo apt install -y python3.11 python3.11-venv python3-pip
                '''
            }
        }
        stage('Exécution du script Python') {
            steps {
                sh '''
                    python3.11 os_detector.py
                '''
            }
        }
    }
    post {
        success {
            mail to: 'charlesdevif@hotmail.fr',
             subject: "Succès de la build Jenkins",
             body: "La build Jenkins s'est terminée avec succès."
        }
        failure {
            mail to: 'charlesdevif@hotmail.fr',
             subject: "Succès de la build Jenkins",
             body: "La build Jenkins s'est terminée avec succès."
        }
    }
}
