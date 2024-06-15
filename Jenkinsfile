pipeline {
    agent any

    stages {
        stage('Cleanup') {
            steps {
                cleanWs()
            }
        }
        stage('Checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/pukarram001/First_one.git']])
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'find ./ -name "*.js" -print0 | xargs -0 /usr/local/bin/jshint > jslint.html || true'
                archiveArtifacts artifacts: 'jslint.html', followSymlinks: false
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'zip -r artifact.zip . -x ".git/*" -x jslint.html'
                archiveArtifacts artifacts: 'artifact.zip', followSymlinks: false
            }
        }
        stage('Deploy') {
            steps {
                 #TO BE COMPLETED BY YOU
            }
        }
    }
}
