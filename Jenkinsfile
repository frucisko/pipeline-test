#!groovy

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
                echo 'Hello World'
            }
        }

        stage('build') {
            steps {
                configFileProvider([configFile(fileId: 'chrome-web-store-props', variable: 'PARAMS')]) {
                    def props = readProperties file: ${env.PARAMS}
                    echo '${props.foo.dev}'
                    sh "cat ${env.PARAMS}"
                }
            }
        }
    }
}
