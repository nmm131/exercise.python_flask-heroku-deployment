pipeline {
    agent {
        docker {
            image 'python' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Set Up') {
            steps {
                script {
                    sh 'rm -rf exercise.python_flask-heroku-deployment'
                }
            }
        }
        stage('SCM Checkout') {
            steps {
                sh 'git clone https://github.com/nmm131/exercise.python_flask-heroku-deployment.git'
                sh 'pip install -r ./exercise.python_flask-heroku-deployment-pipeline/requirements.txt'
            }
        }
        stage('Compile-Package-Test') {
            steps {
                script {
                    dir('./exercise.python_flask-heroku-deployment') {
                        sh "python web.py"
                    }
                }
            }
        }
    }
}
