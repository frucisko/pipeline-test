#!/usr/bin/env groovy

properties = null

def loadProperties(path) {
    node {
        properties = readProperties file: path
        echo "Immediate one ${properties['GOOGLE_CHROME_WEB_STORE_CLIENT_ID']}"
    }
}

pipeline {
    agent {
        docker {
            image 'node:8-alpine'
        }
    }

    options {
        timestamps()
    }

    stages {
        stage('master branch') {
            when {
                branch 'master'
            }
            steps {
                sh 'node -v'
                echo "master branch = ${env.BRANCH_NAME}"
            }
        }

        stage('master dev') {
            when {
                branch 'dev'
            }
            steps {
                echo "dev branch = ${env.BRANCH_NAME}"
            }
        }

        stage('build') {
            steps {
                configFileProvider([configFile(fileId: 'chrome-web-store-props', variable: 'PARAMS')]) {
                    loadProperties(env.PARAMS)
                    echo "${properties['GOOGLE_CHROME_WEB_STORE_CLIENT_ID']}"
                    sh "cat ${env.PARAMS}"
                    // sh 'printenv'
                }
            }
        }
    }
}
