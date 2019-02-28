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
        stage("Building") {
            steps {
                script {
                        echo "Building"
                        // This doesn't work: https://issues.jenkins-ci.org/browse/JENKINS-43370
                        //                    https://issues.jenkins-ci.org/browse/JENKINS-40422
                        githubNotify status: "PENDING", description: "Build is starting...", credentialsId: "github", account: "szumak", repo: "GitHubNotification"
                    }
                }
        }
        stage("Done") {
            steps {
                script {
                        echo "Job is done"
                    }
                }
        }
     }

}
