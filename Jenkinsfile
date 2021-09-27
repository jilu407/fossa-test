node {       
    stage('Git') {
        git 'https://github.com/jilu407/angular-github-actions-s3-deploy.git'
    }
    stage('Build Code') {
        
        sh 'npm install'
    }
    stage('Fossa Analyze') {
        sh 'curl -H \'Cache-Control: no-cache\' https://raw.githubusercontent.com/fossas/fossa-cli/master/install.sh | bash'
        sh '/usr/local/bin/fossa init'
        sh 'FOSSA_API_KEY= fossa analyze'
    }
    }
