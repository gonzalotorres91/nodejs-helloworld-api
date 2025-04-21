pipeline {
    agent any
    tools {
        nodejs 'nodejs21'
    }
    stages {
        stage('Build') {
            steps {
                echo "Ejecutar npm install" 
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo "Ejecutar npm test push" 
                sh 'npm test'
            }
        }
    }
} post {
    success {
        echo 'Build finalizado correctamente.'
    }
    failure {
        echo 'Algo falló. Revisar etapas.'
    }
}
