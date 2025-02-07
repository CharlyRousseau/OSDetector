pipeline {
	agent any
	stages {
		stage('Clonage du dépot github') {
			steps {
				git branch: `main`, url: 'https://github.com/CharlyRousseau/OSDetector.git'
			}
		}
	}
	stage {
        stage('Installation de Python 3.11 et pip') {
            steps {
                sh '''
                    sudo apt update
                    sudo apt install -y python3.11
                '''
            }
        }
    }

    stage('Exécution du script Python') {
            steps {
                sh '''
                python3.11 script.py
                '''
            }
    }

}
