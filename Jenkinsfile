pipeline {
    agent any
    options {
        timestamps()
    }

    stages {
        stage('Init') {
            steps {
                script {
                    if (sh(script: 'docker compose version', returnStatus: true) == 0) {
                        env.COMPOSE = 'docker compose'
                    } else {
                        env.COMPOSE = 'docker-compose'
                    }
                }
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh "${env.COMPOSE} build"
            }
        }
        stage('Test') {
            steps {
                sh "${env.COMPOSE} -p ci up -d --build"
                sh 'curl -fsS http://localhost/healthz'
                sh "${env.COMPOSE} -p ci down -v --remove-orphans"
            }
        }
        stage('Deploy') {
            steps {
                sh "${env.COMPOSE} up -d --build"
            }
        }
    }

    post {
        always {
            sh "${env.COMPOSE} -p ci down -v --remove-orphans || true"
        }
    }
}
