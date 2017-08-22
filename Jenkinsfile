#!groovy

pipeline {
    agent any
    stages {
        stage('configure') {
            steps {
                echo 'Hello World'
            }
        }

        stage('build') {
            steps {
                configFileProvider([configFile(fileId: 'chrome-web-store-props', variable: 'PARAMS')]) {
                    sh "cat ${env.PARAMS}"
                }
            }
        }
    }
}
