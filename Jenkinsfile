// // node{
// //     def buildImage
// //     stage('Build'){
// //             buildImage=docker.image('node:16-buster-slim').run('-p 3000:3000')            
// //         try{
// //             buildImage.inside{
// //                 sh 'npm install'
// //                 }
            
// //         }finally{
// //             if (buildImage != null) {
// //                 buildImage.stop()
// //                 buildImage.remove(force: true)
// //             }
// //         }
// //     }
// // }

// // node{
// //     agent{
// //         docker{
// //             image 'node:16-buster-slim'
// //             args '-p 3000:3000'
// //         }
// //     }
// //     stage('Build'){
// //             sh 'npm install'
// //     }
// // }


// // node {
// //     // Define the Docker image and run the container
// //     def buildImage = docker.image('node:16-buster-slim').run('-p 3000:3000')

// //     try {
// //         // Inside the container, execute the build stage
// //         stage('Build') {
// //             // Run npm install
// //             buildImage.inside {
// //                 sh 'npm install'
// //             }
// //         }
// //     } finally {
// //         // Stop and remove the Docker container after execution
// //         if (buildImage != null) {
// //             buildImage.stop()
// //             buildImage.remove(force: true)
// //         }
// //     }
// // }


// node {
//     def buildImage
//     try{
//         // Define the Docker agent
//             buildImage= docker.image('node:16-buster-slim').run('-p 3000:3000').inside {
//                 // Checkout the Git repository
//                 checkout scm

//                 // Install dependencies and build the React.js project
//                 stage('Build') {
//                     sh 'npm install'
//                     sh 'npm run build'
//                 }

//                 // Optionally, you can add more stages or post-build actions
//                 stage('Test') {
//                     sh 'npm test'
//                 }

//                 // Archive the build artifacts, if needed
//                 archiveArtifacts '**/build/**'
//             }
//     } finally {
//             // Stop and remove the Docker container after execution
//             if (buildImage != null) {
//                 buildImage.stop()
//                 buildImage.remove(force: true)
//             }
//         }
// }
node {
    // Define the Docker agent
    docker.image('node:16-buster-slim').withRun('-p 3000:3000') { c ->
        docker.image('node:16-buster-slim').inside {
            // Checkout the Git repository
            checkout scm

            // Build the React.js project
            stage('Build') {
                sh 'npm install'
                sh 'npm run build'
            }
            stage('Test'){
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}