pipeline {
    agent any

    tools {
        dockerTool 'docker-cli' 
    }

    stages {
        stage('Build') {
            steps {
                echo 'Construyendo el proyecto...'
            }
        }
        stage('Test') {
            steps {
                echo 'Ejecutando pruebas...'
            }
        }
        stage('Security Scan') {
            agent { docker { image 'python:3.9-slim' } } 
            steps {
                echo 'Instalando herramientas de seguridad...'
                sh 'pip install -r requirements.txt'
                echo 'Ejecutando análisis estático con Bandit...'
                sh 'bandit -r . || true' 
            }
        }
    }
}