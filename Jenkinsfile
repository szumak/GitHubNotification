#!/usr/bin/env groovy

pipeline {
    agent any
    stages {
        stage("Start") {
            steps {
                script {
                        echo "Pipeline started"
                    }
                }
        }
        stage("Create secret file") {
            steps {
                script {
                       writeFile file: "config.json", text: credentials('secret.txt'), encoding: "UTF-8"
                    }
                }
        }
        stage("Done") {
            steps {
               sh """
                  cat config.json 
                  """
            }
        }
     }

}
