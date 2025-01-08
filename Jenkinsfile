node {
    def dockerImage

    stage('Clone repository') {
        git branch: 'master',
            credentialsId: 'github_access_token',
            url: 'https://github.com/SonJongKyu/rolling-paper.git'
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
