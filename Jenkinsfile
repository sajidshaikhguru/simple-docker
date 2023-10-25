pipeline {
 environment {
 imagename = “sajidshaikhguru/jenkins-docker”
 registryCredential = ‘adithya-docckerhub’
 dockerImage = ‘’
 }
 agent any
 stages {
 stage(‘cloning’) {
 steps {
 git([url: 'https://github.com/sajidshaikhguru/simple-docker.git', branch: ‘main’])
 }
 }
 stage(‘building image’) {
 steps{
 script {
 dockerImage = docker.build imagename
 }
 }
 }
 stage(‘running image’) {
 steps{
 script {
 sh “docker run ${imagename}:latest”
 }
 }
 }
 stage(‘Deploy Image’) {
 steps{
 script {
 docker.withRegistry( ‘’, registryCredential ) {
 dockerImage.push(“$BUILD_NUMBER”)
 dockerImage.push(‘latest’)
 }
 }
 }
 }
 }
}
