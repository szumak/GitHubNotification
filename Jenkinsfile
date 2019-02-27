#!/usr/bin/env groovy

void setBuildStatus(String message, String state) {
  step([
      $class: "GitHubCommitStatusSetter",
      reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/szumak/GitHubNotification"],
      contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "ci/jenkins/build-status"],
      errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
      statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
  ]);
}

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
                        // githubNotify status: "PENDING", description: "Build is starting...", credentialsId: "github", account: "szumak", repo: "GitHubNotification"
                        setBuildStatus("Build succeeded", "SUCCESS");
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
