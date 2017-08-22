#!groovy

properties = null

def loadProperties(path) {
    node {
        properties = readProperties file: path
        echo "Immediate one ${properties['foo.dev']}"
    }
}

pipeline {
    agent any
    options {
        timestamps()
    }

    stages {
        stage('master branch') {
            when {
                branch 'master'
            }
            steps {
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
                    echo "${properties['foo.dev']}"
                    sh 'printenv'
                }
            }
        }
    }
}
