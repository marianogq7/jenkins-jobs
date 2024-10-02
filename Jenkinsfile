pipeline {
    agent any
    stages {
        stage('Checkout remoto') {
            agent { 
                label 'minikube' 
            }           
            steps {
                script {
                    echo 'Checking out SCM Job Project'
                    git branch: "tp-final",
                    url: 'https://github.com/marianogq7/dds-deploy.git'
                }
            }
        }
        stage('Build Image') {
            steps {
                echo 'Construyendo imagen de Docker...'
                sh 'docker build -t alvarogq/libros .'
            }
        }

    }
}
