pipeline {
    agent{
        label 'AGENT-2'
    }
    /* options{
        // timeout(time:1, unit:'HOUR')
        disableConcurrentBuilds()
    } */
    
    environment{
        DEBUG='true'
        appVersion=''
    }
    stages {
        stage('Read the Version') {
            steps {
                script {
                        def packageJson=readJson file:'package.json'
                        appVersion=packageJson.Version
                        echo "App version:${appVersion}"      
                }
            }
        }
    /*     stage('install the dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('docker build') {
            steps {
                sh """
                docker build -t joindevops/backend:${appversion}
                docker images"""
                }
        }

    } */
    post{
        always{
            echo "This section runs always"
            deleteDir()
        }
    }
}
