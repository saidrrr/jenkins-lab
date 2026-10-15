pipeline {
    agent any

    environment {
        APP_NAME = 'demo-app'
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Récupération du code pour ${APP_NAME}"
                sh 'ls -la'
            }
        }

        stage('Build') {
            steps {
                echo 'Compilation simulée...'
                sh '''
                    mkdir -p build
                    echo "Build ${BUILD_NUMBER} de ${APP_NAME}" > build/resultat.txt
                    cat build/resultat.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Exécution des tests simulés...'
                sh 'test -f build/resultat.txt && echo "Test OK"'
            }
        }
    }

    post {
        always {
            echo 'Pipeline terminé.'
        }
        success {
            echo 'Succès !'
        }
        failure {
            echo 'Échec du pipeline.'
        }
    }
}