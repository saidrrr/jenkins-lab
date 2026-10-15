pipeline {
    agent any
 
    tools {
        maven 'Maven3'
    }
 
    stages {
        stage('Diagnostic') {
            steps {
                sh '''
                    echo "===== JAVA ====="
                    java -version
 
                    echo "===== MAVEN ====="
                    mvn -version
 
                    echo "===== WORKSPACE ====="
                    pwd
                    ls -la
                '''
            }
        }
 
        stage('Build') {
            steps {
                echo 'Build en cours...'
                sh 'mvn clean compile'
            }
        }
 
        stage('Test') {
            steps {
                echo 'Execution des tests unitaires...'
                sh 'mvn test'
            }
        }
    }
 
    post {
        success {
            echo 'Pipeline termine avec succes.'
        }
 
        failure {
            echo 'Echec du pipeline : consulter les logs.'
        }
    }
}