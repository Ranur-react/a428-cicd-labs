node{
 stage('Build'){
    def buildImage
        try{
            buildImage=docker.image('node:16-buster-slim').run('-p 3000:3000')            buildImage.inside{
                sh 'npm install'
                }
            
        }finally{
            if (buildImage != null) {
                buildImage.stop()
                buildImage.remove(force: true)
            }
        }
    }
}