// node{
//     def buildImage
//     stage('Build'){
//             buildImage=docker.image('node:16-buster-slim').run('-p 3000:3000')            
//         try{
//             buildImage.inside{
//                 sh 'npm install'
//                 }
            
//         }finally{
//             if (buildImage != null) {
//                 buildImage.stop()
//                 buildImage.remove(force: true)
//             }
//         }
//     }
// }

pipeline{
    agent{
        docker{
            image 'node:16-buster-slim'
            args '-p 3000:3000'
        }
    }
    stages{
        stage('Build'){
            steps{
                sh 'npm install'
            }
        }
    }
}