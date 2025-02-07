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
            emailext subject: "Build SUCCESS - OSDetector",
                     body: "La build Jenkins s'est terminée avec succès.",
                     to: "charlesdevif@hotmail.fr",
                     attachLog: true
        }
        failure {
            emailext subject: "Build FAILURE - OSDetector",
                     body: "La build Jenkins a échoué. Consultez les logs.",
                     to: "charlesdevif@hotmail.fr",
                     attachLog: true
        }
    }
}
