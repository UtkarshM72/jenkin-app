pipeline {
    agent any

    stages {
        stage('Pull data form git') {
            steps {
                git branch: 'main', url: 'https://github.com/UtkarshM72/jenkin-app.git'
            }
        }
        
        stage('Build Image') {
            steps {
                sh 'ls -l'
                sh 'docker build -t utkarshm72/jen-app .'
            }
        }
        
	stage('Login to Docker Hub') {
            steps {
                # sh 'echo "<dockerhub-token>" | docker login -u <dockerhub-username> --password-stdin'
                sh 'echo "dckr_pat_jws5CRdpGSO2Yc1RwK9VN5I5jSc" | docker login -u utkarshm72 --password-stdin'
            }
        
        }
        
	stage('push image') {
            steps {
                sh 'docker push utkarshm72/jen-app'
            }
        }
	stage('creat service') {
            steps {
                sh 'docker service create --name jen-app -p 4000:4000 --replicas 2 utkarshm72/jen-app'
            }
        }
    }
}

