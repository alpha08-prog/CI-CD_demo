stage('Push to Registry') {
    steps {
        withCredentials([usernamePassword(
            credentialsId: 'docker-hub-credentials',
            usernameVariable: 'DOCKER_USER',
            passwordVariable: 'DOCKER_PASS'
        )]) {
            bat """
                docker logout
                docker login -u %DOCKER_USER% -p %DOCKER_PASS%
                docker push ${REGISTRY}:${IMAGE_TAG}
                docker tag ${REGISTRY}:${IMAGE_TAG} ${REGISTRY}:latest
                docker push ${REGISTRY}:latest
            """
        }
    }
}
