node {
    stage('Clone repository') {
        git credentialsId: 'github-access', url: 'https://github.com/SonJongKyu/rolling-paper'
    }
    stage('Build image') {
        dockerImage = docker.build("sonjong/node-front:1.0")
    }
    stage('Push image') {
        withDockerRegistry([ credentialsId: "docker-access", url: "" ]) {
            dockerImage.push()
        }
    }
}
