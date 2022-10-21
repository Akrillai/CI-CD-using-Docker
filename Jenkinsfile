pipeline {
    agent any
	
	  tools
    {
       maven "m3"
    }
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/devops4solutions/CI-CD-using-Docker.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t samplewebapp:latest .' 
                //sh 'docker tag samplewebapp nikhilnidhi/samplewebapp:latest'
                //sh 'docker tag samplewebapp nikhilnidhi/samplewebapp:$BUILD_NUMBER'
               
          }
        }
     

 stage('Run Docker container on remote hosts') {
             
            steps {
                sh '''ssh root@172.31.3.13 << EOF
		docker run -d -p 8004:8080 nikhilnidhi/samplewebapp
        EOF'''

            }
        }
    }
	}
