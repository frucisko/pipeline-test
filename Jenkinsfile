#!groovy

pipeline {
    agent any
    def configFile = 'chrome-web-store-props'

    stages {
        stage('Example') {
            steps {
                echo 'Hello World'
            }
        }

        stage('configFile Plugin') {
            steps {
                configFileProvider([configFile(fileId: configFileProvider, variable: 'PARAMS')]) {
                    echo " =========== ^^^^^^^^^^^^ Reading config from pipeline script "
                    sh "cat ${env.PARAMS}"
                    echo " =========== ~~~~~~~~~~~~ ============ "
                }
            }
        }
    }
}
