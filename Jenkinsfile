//CODE_CHANGE = getGitChanges{} create groovy script. 
pipeline {
  agent any
  environment{
     //define environment variables in the pipeline here 
     //jenkins environment variables - localhost:8080/env-vars.html 
    NEW_VERSION = '1.2.0' //normally you would extract this info and increment
    //SERVER_CREDENTIALS = credentials('credentialID') //Binds the credentails, you need to install the credentials binding plugin, takes the id referrence for the credentials. 
  }
  tools{
  }
  stages {
    stage('Build') {
      when {
        expression{
            (BRANCH_NAME == "development" || BRANCH_NAME == "master")  //&& CODE_CHANGE == true      
        }  
      }
      steps {
        echo 'I am in the build stage'
        echo "Building Version ${NEW_VERSION}" 
        git(url: 'https://github.com/ayalgul/juice-shop.git', branch: 'master')
      }
    }

    stage('Test') {
      when {
        expression{
            BRANCH_NAME == "development"
        }  
      }   
      steps {
        echo 'I am in the Test Stage '
      }
    }

    stage('Deploy') {
      steps {
        echo 'I am in the Deploy stage '
        //used to extract credentials 
        //withCredentials([
        //     usernamePassword(credentials: 'credential_id', usernameVariable: USER, passwordVariable: PASS)
        //]){
            //sh "some script to extract info ${USER} $PASS}" 
        //}
          
      }
    } 
  }
  post{
      always{
          //this posts always after the build pipeline no matter what can be used for monitoring. 
      }
  }
  success{
    // runs when the pipeline is succesfull
  }
  failure{
    //runs when the pipeline is a failure. 
  }
}
