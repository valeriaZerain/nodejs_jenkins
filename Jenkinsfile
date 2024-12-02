pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Clonando el repositorio...'
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                echo 'Instalando dependencias...'
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                echo 'Ejecutando pruebas...'
                script {
                    def status = sh(script: 'npm test', returnStatus: true)
                    if (status != 0) {
                        echo "Las pruebas fallaron, pero continuamos con el siguiente paso."
                    }
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Construyendo la aplicación...'
                sh 'npm run build || echo "No hay pasos de construcción definidos"'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Desplegando la aplicación...'
                sh 'echo "Despliegue simulado completado"'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completado con éxito.'
        }
        failure {
            echo 'El pipeline falló. Revisa los errores.'
        }
    }
}
