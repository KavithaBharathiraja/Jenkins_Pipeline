pipeline {
    agent none
    stages {
        stage('Build and Run') {
            parallel {
                stage('master-agent-pipeline') {
                    agent { label 'master' }
                    stages {
                        stage('Build') {
                            steps {
                                echo 'Building on master agent..'
                                sh 'mvn clean install'
                                // Add additional build steps here
                            }
                        }
                        stage('Test') {
                            steps {
                                echo 'Testing on master agent..'
                                sh 'mvn test'
                                // Add additional test steps here
                            }
                        }
                    }
                }
                stage('ubuntu-agent-pipeline') {
                    agent { label 'ubuntu' }
                    stages {
                        stage('Build') {
                            steps {
                                echo 'Building on Ubuntu agent..'
                                sh 'mvn clean install'
                                // Add additional build steps here
                            }
                        }
                        stage('Test') {
                            steps {
                                echo 'Testing on Ubuntu agent..'
                                sh 'mvn test'
                                // Add additional test steps here
                            }
                        }
                    }
                }
            }
        }
    }
}
