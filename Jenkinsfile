node{
    def buildImage
    buildImage=docker.image('node:16-buster-slim').run('-p 3000:3000')
        stage('Build'){
            buildImage.inside{
            sh 'npm install'
            }
        }
    // try{
    //     buildImage=docker.image('node:16-buster-slim').run('-p 3000:3000')
    //     stage('Build'){
    //         buildImage.inside{
    //         sh 'npm install'
    //         }
    //     }
    // }finally{
    //     if (buildImage != null) {
    //         buildImage.stop()
    //         buildImage.remove(force: true)
    //     }
    // }
}