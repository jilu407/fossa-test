node {   def registry = 'registry.hub.docker.com/xxxxxx/test'
   def registryCredential = 'dockerhub'
    
    stage('Git') {
        git 'https://github.com/jilu407/angular-github-actions-s3-deploy.git'
    }
    stage('Build Code') {
        
        sh 'npm install'
    }
    stage('Fossa Analyze') {
        sh 'curl -H \'Cache-Control: no-cache\' https://raw.githubusercontent.com/fossas/fossa-cli/master/install.sh | bash'
        sh 'fossa init'
        sh 'FOSSA_API_KEY=XXXXXXXXXXXXXXXXXXXX fossa analyze'
    }
    stage('Building image') {
       docker.withRegistry( 'https://' + registry, registryCredential ) {
            def buildName = registry + ":$BUILD_NUMBER"
            newApp = docker.build buildName
            newApp.push()
       }
    }
    stage('Registering image') {
       docker.withRegistry( 'https://' + registry, registryCredential ) {
           newApp.push 'latest2'
       }
    }
   stage('Removing Local image') {
       sh "docker rmi $registry:$BUILD_NUMBER"   }}
   }
}