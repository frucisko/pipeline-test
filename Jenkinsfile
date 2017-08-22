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
                step {
                    // 'ID' refers to alpha-numeric value generated automatically by Jenkins.
                    // This code snippet assumes that the config file is stored in Jenkins.

                    // help to assign the ID of config file to a variable, this is optional
                    // as ID can be used directly within 'configFileProvider' step too.
                    def configFile = 'chrome-web-store-props'

                    // whether referencing the config file as ID (directly) or via user-defined
                    // variable, 'configFileProvider' step enables access to the config file
                    // via 'name' given for the field, 'variable:'
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
