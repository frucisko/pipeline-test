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
            steps {
                configFileProvider([configFile(fileId: 'chrome-web-store-props', variable: 'PARAMS')]) {
                    echo " =========== ^^^^^^^^^^^^ Reading config from pipeline script "
                    sh "cat ${env.PARAMS}"
                    echo " =========== ~~~~~~~~~~~~ ============ "
                }
            }
        }
    }
}
