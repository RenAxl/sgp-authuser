pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-11-openjdk'
        PATH = "${env.PATH}:${env.JAVA_HOME}/bin"
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Fazendo checkout do código...'
                git branch: 'main', url: 'https://github.com/RenAxl/sgp-authuser.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Iniciando o Build...'
                sh './mvnw clean install'
            }
        }

        stage('Package') {
            steps {
                echo 'Empacotando Aplicação...'
                sh './mvnw package'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy Finalizado. Artefato disponível no diretório target.'
            }
        }
    }

    post {
        success {
            echo 'Build finalizado com sucesso!'
        }
        failure {
            echo 'Erro durante o Build!'
        }
    }
}
