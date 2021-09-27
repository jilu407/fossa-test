node {       
    stage('Git') {
        git 'https://github.com/jilu407/fossa-test.git'
    }
    stage('Build Code') {
        
    }
    stage('Fossa Analyze') {
        sh '''
        
        curl -H \'Cache-Control: no-cache\' https://raw.githubusercontent.com/fossas/fossa-cli/master/install.sh | bash
        /usr/local/bin/fossa init' && sr/local/bin/fossa FOSSA_API_KEY=hfda8f189521174286901f6cd34eabfc7 fossa analyze
        '''
    }
    }
