pipeline {

agent any

stages {


stage('Checkout') {
steps {
git branch: 'main',
url: 'https://github.com/3012akash/devops-training-project.git'
}
}


stage('Build Docker Image') {
steps {
sh '''
docker build -t aakashg1230/devops-training-image:v3 .
'''
}
}


stage('Push Image') {
steps {
sh '''
docker push aakashg1230/devops-training-image:v3
'''
}
}


stage('Deploy Kubernetes') {
steps {

sh '''
kubectl set image deployment/devops-training-deployment \
devops-training-container=aakashg1230/devops-training-image:v3
'''

}
}


stage('Verify Deployment') {
steps {

sh '''
kubectl rollout status deployment/devops-training-deployment
kubectl get pods
kubectl get svc
'''

}

}


}

}
