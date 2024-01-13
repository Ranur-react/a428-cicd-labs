
node {
    docker.image('node:16-buster-slim').withRun('-p 3000:3000') { c ->
        docker.image('node:16-buster-slim').inside {
            checkout scm
            stage('Build') {
                sh 'npm install'
                sh 'npm run build'
            }
            stage('Test'){
                sh './jenkins/scripts/test.sh'
                junit 'test-reports/results.xml'
            }
    
        }
    }
}