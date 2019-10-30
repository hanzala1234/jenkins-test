node{
   def image 
    stage('checkout'){
                 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'bitbucket-creds', url: 'https://bitbucket.org/fairytalyo/fairy-endgame.git']]])
    }
       
    stage('Building docker images'){
        sh "SHA=$(git rev-parse HEAD)"
        sh "docker build -t eu.gcr.io/fairylend-dev/fairy-client:${SHA} client/"
        
        
        
    }
//     stage('Pushing docker images'){
//         withDockerRegistry(credentialsId: 'DOCKER_ID') {
//             image.push("v${env.BUILD_ID}");

// }

//    stage('running Docker container'){
// 	image.run('-d -p 8060:8060')

// }
    
}

