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

// node{
//     agent{
//         docker{
//             image 'node:16-buster-slim'
//             args '-p 3000:3000'
//         }
//     }
//     stage('Build'){
//             sh 'npm install'
//     }
// }


node {
    // Define the Docker image and run the container
    def buildImage = docker.image('node:16-buster-slim').run('-p 3000:3000')

    try {
        // Inside the container, execute the build stage
        stage('Build') {
            // Run npm install
            buildImage.inside {
                sh 'npm install'
            }
        }
    } finally {
        // Stop and remove the Docker container after execution
        if (buildImage != null) {
            buildImage.stop()
            buildImage.remove(force: true)
        }
    }
}
