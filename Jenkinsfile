pipeline {
    agent any
 
    tools {
        maven 'Maven3'
    }
 
    stages {
        stage('Diagnostic') {
            steps {
                sh '''
                    java -version
                    mvn -version
                    ls -la
                    ls -la demo-app
                '''
            }
        }
 
        stage('Build') {
            steps {
                dir('demo-app') {
                    echo 'Build Maven en cours...'
                    sh 'mvn clean compile'
                }
            }
        }
 
        stage('Test') {
            steps {
                dir('demo-app') {
                    echo 'Execution des tests unitaires...'
                    sh 'mvn test'
                }
            }
        }
    }
 
    post {
        success {
            echo 'Build et tests termines avec succes.'
        }
 
        failure {
            echo 'Echec du pipeline : consulter les logs.'
        }
    }
}