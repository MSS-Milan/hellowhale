pipeline {

  agent any
    def registry = 'milan2312/hellowhale
    def registryCredential = 'dockerhub'

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/milanoo7/hellowhale.git', branch:'master'
      }
    }
    
      stage("Build image") {
            steps {
                script {
                    myapp = docker.build("milan2312/hellowhale:${env.BUILD_ID}")
                }
            }
        }
    
   stage('Building image') {
        docker.withRegistry( 'https://' + registry, registryCredential ) {
		    def buildName = registry + ":$BUILD_NUMBER"
			newApp = docker.build buildName
			newApp.push()
        }
	}

    


  }

}
