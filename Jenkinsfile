pipeline {
    agent {
        label 'python'
    }

    stages {
        stage('download the source repo') {
            steps {
                git branch: 'main', url: 'https://github.com/ArunChaitanya93/Python.git'
            }
        }
        stage('install python, pip and requirements') {
            steps {
                sh 'yum install python -y'
                sh 'yum install python-pip -y'
                sh 'pip install -r requirements.txt'
            }
        }
        stage('flake8 and unit test cases') {
            steps {
                sh 'python -m flake8 --max-line-length=100 --ignore=E501,E402,E731,E722,E261,E265,E303,E501 .'
                sh 'pytest'
            }
        }
        stage('build docker image') {
            steps {
                sh 'docker build -t pythonapp:latest .'
            }
        }
        stage('run docker container') {
            steps {
                sh 'docker rm -f webos'
                sh 'docker run -d --name webos -p 80:80 pythonapp:latest'
            }
        }
        
    }
}