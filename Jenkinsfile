pipeline {
environment {
registry = '19kshitij/test1'
registryCredential = 'docker'
}
agent any
stages {
stage('Cloning Git') {
 steps {
 git "https://github.com/kshitijtest/anchoretest.git"
 }}
stage('Building image') {
 steps{
 script {
 dockerImage = docker.build registry + “$BUILD_NUMBER”}}}
stage('Container Security Scan') {
 steps {
 sh "echo 'docker.io/19kshitij/test1 'pw'/Dockerfile' > anchore_images"
 anchore name: ‘anchore_images’}}
stage('Deploy Image') {
 steps{
 script {
 docker.withRegistry( '', registryCredential )
 dockerImage.push()
 }}
}}}
