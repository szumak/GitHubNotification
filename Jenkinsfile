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
                       withCredentials([[$class: 'FileBinding', credentialsId: 'configuration_test', variable: 'SECRET_FILE']]) {
                           sh 'ls -al $SECRET_FILE'
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
