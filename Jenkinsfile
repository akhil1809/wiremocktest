node {
    stage('GitSCM  Checkout')
    {
        git branch: 'main', credentialsId: 'gitcred', url: 'https://github.com/akhil1809/wiremocktest.git'
        
    }
    stage('Stage Build Docker Image')
    {
        sh 'docker build -t akhil1809/wiremocktest .'
    }
    stage("Push Docker image to Docker hup")
    {
        sh 'docker push akhil1809/wiremocktest'
    }
   stage("Run container on awswiermockserver")
   {
       def dockerRunCommand = 'docker run -p 8080:8080 --name wiremock-test akhil1809/wiremocktest'
       sshagent(['wiremock_dev']) 
       {
          sh "ssh -o StrictHostKeyChecking=no ec2-user@3.15.183.103 ${dockerRunCommand}"
          
       }  
   }
}