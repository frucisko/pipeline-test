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
        stage('configure') {
            when {
                branch 'master'
            }
            steps {
                echo 'master branch'
            }
        }

        stage('build') {
            steps {
                configFileProvider([configFile(fileId: 'chrome-web-store-props', target: 'config', variable: 'PARAMS')]) {
                    loadProperties(env.PARAMS)
                    echo "${properties['foo.dev']}"
                    sh "cat ${env.PARAMS}"
                }
            }
        }
    }
}
