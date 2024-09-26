pipeline {
agent any
parameters {
choice(
name: 'ENVIRONMENT',
choices: ['dev', 'qa', 'prod'],
description: 'Select the deployment environment'
)
}
stages {
stage('SCM code') {
steps {
git 'https://github.com/hellokaton/java11-examples.git'
}
}
stage('Build') {
steps {
sh 'mvn clean package'
}
}
stage('Publish') {
when {
expression { params.ENVIRONMENT == 'prod' }
}
steps {
// Add steps to publish artifacts or deploy the application for 'prod'
// For example, you can use the 'archiveArtifacts' step to archive built artifacts
archiveArtifacts 'target/*.jar'
}
}
}
}
