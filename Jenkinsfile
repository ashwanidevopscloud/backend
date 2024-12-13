pipeline {
    options{
        timeout(time:10, unit:'SECONDS')
        disableConcurrentBuilds()
    }
    parameters{
        string(name:'PERSON', defaultValue:'Mr Jenkins', description:'Who should I say hello to?')
    }
    environment{
        DEBUG='true'
        appVersion=''
    }
    stages {
        stage('Read the Version') {
            steps {
                script{
                def packagejson=readJson file:'package.json'
                appVersion=packagejson.Version
                echo "App version:${appVersion}"
                }
            }
        }
        stage('install the dependencies') {
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
        stage('Test') {
            steps {
                sh 'echo this is Test'  
                sh 'env'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo this is deploy'
            }
        }
        stage('Print Params'){
            steps{
                echo "Hello ${params.PERSON}"
            }
        }

    }
    post{
        always{
            echo "This section runs always"
            deleteDir()
        }
    }
}
