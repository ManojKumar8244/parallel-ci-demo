pipeline {
    agent { label 'agent-1' }

    tools {
        maven 'Maven-3'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ManojKumar8244/parallel-ci-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Parallel Tests') {
            parallel {
                stage('Unit Tests') {
                    steps {
                        sh 'mvn test'
                    }
                }
                stage('Integration Tests') {
                    steps {
                        sh 'mvn verify'
                    }
                }
                stage('Code Analysis') {
                    steps {
                        echo 'Code analysis running...'
                    }
                }
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }
}