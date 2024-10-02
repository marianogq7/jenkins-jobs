pipeline {
    agent any
    stages {
        stage('Checkout Jenkinsfile Repo') {
            steps {
                script {
                    echo 'Cloning Jenkinsfile repo...'
                    git branch: "main",
                        url: 'https://github.com/marianogq7/jenkins-jobs.git'
                }
            }
        }

        stage('Checkout App Repo') {
            agent { 
                label 'minikube' 
            }
            steps {
                dir('app') {  // Clonar el repositorio de la app en una subcarpeta llamada 'app'
                    script {
                        echo 'Cloning App Repo...'
                        git branch: "tp-final",
                            url: 'https://github.com/marianogq7/dds-deploy.git'
                    }
                }
            }
        }

        stage('Build Image') {
            agent { 
                label 'minikube' 
            }
            steps {
                dir('app') { // Cambia al directorio 'app' antes de construir la imagen
                    echo 'Construyendo imagen de Docker...'
                    sh 'ls -l'
                    sh 'pwd'
                    sh 'docker build -t alvarogq/libros .'
                }
            }
        }
    }
}
