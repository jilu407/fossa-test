pipeline{
agent any
  environment {
    PATH = "$PATH:/usr/lib/go-1.12/bin:/usr/local/go/bin/:$WORKSPACE/go/bin"
    GOPATH = "$WORKSPACE/go"
  }
stages 
{
stage('Build') 
{
steps{
  sh '''
		      echo "Download/install fossa CLI tool"
              curl -H 'Cache-Control: no-cache' -O https://raw.githubusercontent.com/fossas/fossa-cli/master/install.sh
              mkdir -p "$WORKSPACE/go/bin"
              bash install.sh -b "$WORKSPACE/go/bin"
			  echo "Fossa version:"
              fossa -v
			  fossa init
			  FOSSA_API_KEY=hfda8f189521174286901f6cd34eabfc7 fossa analyze
			  
		'''
}
}

}
}