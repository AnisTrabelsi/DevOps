pipeline {
    agent any

    tools {
        maven 'Maven3' // Doit correspondre au nom configuré dans "Global Tool Configuration"
    }

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Cloner le dépôt') {
            steps {
                checkout scm
                // Ou, si tu veux forcer un dépôt :
                // git url: 'https://github.com/AnisTrabelsi/DevOps.git', branch: 'main'
            }
        }

        stage('Nettoyage Maven') {
            steps {
                sh 'mvn clean'
            }
        }

        stage('Compilation Maven') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test Maven') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Afficher version Maven & Java') {
            steps {
                sh 'mvn -version'
                sh 'java -version'
            }
        }
    }

    post {
        success {
            echo 'Pipeline terminé avec succès.'
        }
        failure {
            echo 'La pipeline a échoué.'
        }
        always {
            echo 'Pipeline terminée (succès ou échec).'
        }
    }
}

