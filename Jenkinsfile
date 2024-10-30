pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    def app = docker.build("nodejs-api")
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    def app = docker.image("nodejs-api")
                    app.inside {
                        sh 'npm test'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    def app = docker.image("nodejs-api")
                    app.run("-d -p 3000:3000")
                }
            }
        }
    }
}
