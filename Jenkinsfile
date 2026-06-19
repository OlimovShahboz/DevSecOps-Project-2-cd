pipeline {
 agent any
 parameters {
     password(name: 'PASSWD', defaultValue: '', description: 'Please Enter your GitHub password/token')
     string(name: 'IMAGETAG', defaultValue: '1', description: 'Please Enter the Image Tag to Deploy?')
 }
 stages {
  stage('Deploy')
  {
    steps { 
        git branch: 'main', credentialsId: 'GitlabCred', url: 'https://github.com/OlimovShahboz/DevSecOps-Project-2-cd.git'
      dir ("./kubernetes") {
              sh "sed -i 's/image: shahboz01.*/image: shahboz01\\/democicd:$IMAGETAG/g' deployment.yml" 
	    }
	    sh 'git commit -a -m "New deployment for Build $IMAGETAG"'
	    sh "git push https://OlimovShahboz:$PASSWD@github.com/OlimovShahboz/DevSecOps-Project-2-cd.git"
    }
  }
 }
}
