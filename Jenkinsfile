pipeline {
    agent any

    environment {
        NVM_DIR = "$HOME/.nvm"
        NODE_VERSION = "21.1.0"
    }

    stages {
        stage('Preparar entorno Node') {
            steps {
                sh '''
                export NVM_DIR="$HOME/.nvm"
                [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                nvm install $NODE_VERSION
                nvm use $NODE_VERSION
                node -v
                npm -v
                '''
            }
        }

        stage('Instalar dependencias') {
            steps {
                sh '''
                export NVM_DIR="$HOME/.nvm"
                [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                nvm use $NODE_VERSION
                npm install
                '''
            }
        }

        stage('Ejecutar tests') {
            steps {
                sh '''
                export NVM_DIR="$HOME/.nvm"
                [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                nvm use $NODE_VERSION
                npm test
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build completado con éxito.'
        }
        failure {
            echo '❌ Falló el build. Revisar los logs.'
        }
    }
}
