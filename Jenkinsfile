pipeline {

    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
        packageVersion = ''
     }
    // build
    options{
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
    }


    stages {
        stage('Get the version') {
            steps {
                script{
                    def packageJson = readJSON file: 'package.json'
                    packageVersion = packageJson.version
                    echo "application version: $packageVersion"
                }
            }
        }
        stage('Install dependencies') {
            steps {
                sh """
                    npm install
                """
            }
        }
        stage('Build') {
            steps {
                sh """
                    ls -la
                    zip -r catalogue.zip ./* -x ".git" -x "*.zip"
                    ls -ltr
                """
            }
        }
        stage('Deploy') {
            steps {
                sh """
                    echo 'Here i wrote shell script'
                    
                """
            }
        }
    }
    //post build
    post {
        always {
            echo "I will always say Hello again!"
            deleteDir()
        }
        failure {
            echo 'This runs when pipe line is failed, used generaly to send some alerts.'
        }
        success {
            echo ' I will say Helo when piope line is success.'
        }
    }
}