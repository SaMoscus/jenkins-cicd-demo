
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker image'
                sh 'docker build -t jenkins-cicd-demo:${BUILD_NUMBER} .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing the website files'
                sh 'test -s app/index.html'
                sh 'grep -q "Jenkins CI/CD Demo" app/index.html'
                echo 'Website tests passed!'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application with Docker'

                sh '''
                    docker rm -f jenkins-cicd-demo || true

                    docker run -d \
                        --name jenkins-cicd-demo \
                        -p 8082:80 \
                        jenkins-cicd-demo:${BUILD_NUMBER}
                '''
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Build, test and deployment completed!'
        }

        failure {
            echo 'FAILED: Check the Jenkins Console Output.'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
