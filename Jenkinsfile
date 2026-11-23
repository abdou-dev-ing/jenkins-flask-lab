pipeline {
agent any
environment {
IMAGE_NAME = 'jenkins-flask-lab'
CONTAINER_NAME = 'jenkins-flask-app'
APP_PORT = '8081'
}
stages {
stage('Checkout') {
steps {
echo 'Source code is available in the workspace.'
}
}
stage('Build') {
steps {
sh 'docker build -t 𝐼𝑀𝐴𝐺𝐸𝑁𝐴𝑀𝐸:{BUILD_NUMBER} .'
}
}
stage('Test') {
steps {
sh 'docker run --rm 𝐼𝑀𝐴𝐺𝐸𝑁𝐴𝑀𝐸:{BUILD_NUMBER} pytest -v'
}
}
stage('Deploy') {
steps {
sh '''
docker rm -f ${CONTAINER_NAME} || true
docker run -d --name ${CONTAINER_NAME} -p 𝐴𝑃𝑃𝑃𝑂𝑅𝑇: 8000 − 𝑒𝐴𝑃𝑃𝑉𝐸𝑅𝑆𝐼𝑂𝑁 =
{BUILD_NUMBER} 𝐼𝑀𝐴𝐺𝐸𝑁𝐴𝑀𝐸:{BUILD_NUMBER}
'''
}
}
stage('Verify') {
steps {
sh 'curl --fail --retry 10 --retry-delay 2 http://localhost:${APP_PORT}/health'
sh 'curl --fail http://localhost:${APP_PORT}/'
}
}
}
post {
success {
echo 'Pipeline completed successfully.'
}
failure {
echo 'Pipeline failed. Check the stage that reported an error.'
}
}
}
