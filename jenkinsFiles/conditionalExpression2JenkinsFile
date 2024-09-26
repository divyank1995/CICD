pipeline {
agent any
parameters {
choice(
name: 'ENVIRONMENT',
choices: ['dev', 'qa', 'prod'],
description: 'Select the deployment environment'
)
choice(
name: 'PRIORITY',
choices: ['high', 'low', 'middle'],
description: 'Select the priority'
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
stage('Publish High Priority') {
when {
expression { params.ENVIRONMENT == 'prod' && params.PRIORITY == 'high' }
}
steps {
// Add steps to publish high-priority artifacts or deploy the application for 'prod'
// For example, you can use the 'archiveArtifacts' step to archive built artifacts
archiveArtifacts 'target/*.jar'
}
}
stage('Publish Low Priority') {
when {
expression { params.ENVIRONMENT == 'prod' && params.PRIORITY == 'low' }
}
steps {
// Add steps to publish low-priority artifacts or deploy the application for 'prod'
// For example, you can use the 'archiveArtifacts' step to archive built artifacts
archiveArtifacts 'target/*.jar'
}
}
stage('Publish Middle Priority') {
when {
expression { params.ENVIRONMENT == 'prod' && params.PRIORITY == 'middle' }
}
steps {
// Add steps to publish middle-priority artifacts or deploy the application for 'prod'
// For example, you can use the 'archiveArtifacts' step to archive built artifacts
archiveArtifacts 'target/*.jar'
}
}
}
}
