node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("webtechnelson/ci-test-image")
    }
    stage('Test image') {
        app.inside {
            sh 'echo "Tests passed"'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BUILD_NUMBER}")
        }
    }
    stage('Trigger ManifestUpdate') {
        echo "triggering updatek8PipelineGitOps job"
        build job: 'updatek8PipelineGitOps', parameters: [string(name: 'DOCKERTAG', value: env.BUILD_NUMBER)]
    }
}