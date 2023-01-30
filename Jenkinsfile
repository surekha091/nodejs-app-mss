pipeline {
    agent {
        node {
            label 'node'
        }
    }
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/user/project.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'yarn install'
            }
        }
        stage('Build') {
            steps {
                sh 'yarn build'
            }
        }
        stage('Test') {
            steps {
                sh 'yarn test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'ftp -p -i -v -n $FTP_HOST <<EOF
                user $FTP_USERNAME $FTP_PASSWORD
                put -r dist/*
                quit
                EOF'
            }
        }
    }
