pipeline {
    agent any // Or specify the agent label/nodes where the pipeline should run 
    stages {
        stage('Build Service 1') {
            steps {
                dir('django-notes-app') {
                    // Build the Docker image for service1
                    sh 'docker build -t Shiba07s/django-notes-app:latest .'
}
            }
        } 

        stage('Build Service 2') {
            steps {
                dir('django-todo-cicd') {
                    // Build the Docker image for service2
                    sh 'docker build -t Shiba07s/django-todo-cicd:latest .'
                }
            }
        } 

        // stage('Unit Tests') {
        //     steps {
        //         dir('service1') {
        //             // Run unit tests for service1
        //             sh 'npm test'
        //         }

 

        //         dir('service2') {
        //             // Run unit tests for service2
        //             sh 'pytest'
        //         }
        //     }
        // } 

         stage("Deploy"){
            steps {
                echo "Deploying the container"
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
post {
        success {
            echo 'CI/CD process completed successfully!'
        }
        failure {
            echo 'CI/CD process failed!'
        }
    }
    }
