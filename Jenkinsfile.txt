pipeline {
    agent any

    tools {
        maven 'Maven3' // Le nom doit correspondre à ton outil Maven défini dans Jenkins
    }

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        PATH = "$JAVA_HOME/bin:$PATH"
    }

    stages {
        stage('Cloner le dépôt') {
            steps {
                git 'https://github.com/AnisTrabelsi/DevOps.git'
            }
        }

        stage('Compilation Maven') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test Maven') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Affichage version') {
            steps {
                sh 'mvn -version'
            }
        }
    }
}
