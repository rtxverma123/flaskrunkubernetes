node {
    stage('Get Source'){
        git ''
        
    }
    stage('Docker-build'){
        sh 'docker build '
    }
    stage('Docker-push'){
        docker.withRegistry('https://registry.hub.docker.com','Docker'){
            def customImage = docker.build('rtxverma123/jenkinsnewflaskpush')
            customImage.push()
        }
    }
    stage('Kubernetes pod'){
        sh 'kubectl apply -f servicepy.yaml'
        sh 'kubectl apply -f flask-deployment.yaml'
        sh 'kubectl get pods'
    }
}