pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      agent any
      steps {
        sh 'tidy -q -e *.html'
      }
    }

  }
  stage('Build Docker Image') {
			steps {
				withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD']]){
					sh '''
						docker build -t rocky20/capstone .
					'''
				}
			}
		}
}
