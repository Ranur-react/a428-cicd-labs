node{
    def buildImage
    buildImage=docker.image('node:16-buster-slim').withRun('-p 3000:3000')
    stage('Build'){
        buildImage.inside{
         sh 'npm install'
        }
    }
}