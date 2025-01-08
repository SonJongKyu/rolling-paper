node {
    def dockerImage // Docker 이미지 변수 선언

    stage('Clone repository') {
        // Git 저장소에서 코드 클론
        git branch: 'master',
            credentialsId: 'github_access_token',
            url: 'https://github.com/SonJongKyu/rolling-paper.git'
    }

    stage('Build image') {
        // Docker 이미지 빌드
        dockerImage = docker.build("sonjong/node-front:1.0")
    }

    stage('Push image') {
        // Docker Hub에 이미지 푸시
        withDockerRegistry([credentialsId: "docker-access", url: "https://index.docker.io/v1/"]) {
            dockerImage.push()
        }
    }
}

