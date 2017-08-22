#!groovy

pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                echo 'Hello World'
            }
        }

        stage('configFile Plugin') {
            def configFile = 'chrome-web-store-props'
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
}
