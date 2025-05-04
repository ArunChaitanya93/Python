pipeline {
    agent {
        label 'gfgpython'
    }

    stages { //collection of jobs
        stage('Deployment') { //stage == job
            steps { // job steps
              sh 'docker pull jinny1/gfgdevops33:latest'
              sh 'docker rm -f gfgwebos'
              sh 'docker run -d --name gfgwebos -p 80:80 jinny1/gfgdevops33:latest'
        }
            }
        }
    }
   