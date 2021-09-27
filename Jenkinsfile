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
		'''
}
}
stage('Test') 
{
steps{
echo "Testing the Code.........."

}
}
stage('Compile') 
{
steps{
echo "Compiling the Project.........."

}
}
stage('Deploy') 
{
steps{
echo "Deploying the Project.........."
}
}
}
}