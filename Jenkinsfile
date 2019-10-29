node{
   def image 
    stage('checkout'){
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/hanzala1234/jenkins-pract.git']]])
                 
    }
    stage('Building docker images'){
        sh 'ls'
        sh "docker info" 
        image = docker.build("muhammadhanzala/jenkins-demo:${env.BUILD_ID}")
        
    }
    stage('Pushing docker images'){
        withDockerRegistry(credentialsId: 'DOCKER_ID') {
            image.push("v${env.BUILD_ID}");

}
   stage('removing old container'){
 	sh label: '', script: '''docker ps -a | awk \'{ print $1,$2 }\' | grep -i muhammadhanzala/jenkins-demo | awk \'{ print $1 }\' | xargs docker stop
'''
    }
   stage('running Docker container'){
	image.run('-d -p 8060:8060')

}
    }
}
