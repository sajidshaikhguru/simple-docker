pipeline {
 environment {
 imagename = “sajidshaikhguru/jenkins-docker”
 registryCredential = ‘sajidshaikhguru’
 dockerImage = ‘mama’
 }
 agent any
 stages {
 stage(‘cloning’) {
 steps {
 git([url: 'https://github.com/sajidshaikhguru/simple-docker.git', branch: ‘main’])
 }
 }
 stage(‘building’) {
 steps{
 script {
 dockerImage = docker.build imagename
 }
 }
 }
 stage(‘running_image’) {
 steps{
 script {
 sh “docker run $imagename:latest”
 }
 }
 }
 stage(‘deploy_image’) {
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
