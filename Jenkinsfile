pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
         stage('Clone repository') {
            steps {
                script{
                checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                script{
                 app = docker.build("my-demo-docker-repo")
                }
            }
        }
        stage('Test'){
            steps {
                 echo 'Empty'
            }
        }
        stage('Deploy') {
            steps {
                script{
                        docker.withRegistry('https://936176622875.dkr.ecr.us-east-1.amazonaws.com/', 'ecr:us-east-1:DemoJenkinUser') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                    }
                }
            }
        }
    }
}