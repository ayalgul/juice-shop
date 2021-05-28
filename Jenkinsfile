//CODE_CHANGE = getGitChanges{} create groovy script. 
pipeline {
  agent any
  environment{
     //define environment variables in the pipeline here 
     //jenkins environment variables - localhost:8080/env-vars.html 
    NEW_VERSION = '1.2.0' //normally you would extract this info and increment
    //SERVER_CREDENTIALS = credentials('credentialID') //Binds the credentails, you need to install the credentials binding plugin, takes the id referrence for the credentials. 
  }
  parameters{
     //string(name:'VERSION' defaultValue: '1.2.0' description: 'version to deploy on prod')
     //choices(name:'VERSION' choices['1.0','1.1', '1.2'])
     booleanParam(name: 'executeTest', defaultValue: true, description: 'version to deploy on prod')
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
        sh 'npm install'
      }
    }

    stage('Test') {
      when {
        expression{
            params.executeTest == true 
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
          echo 'done with Build
      }
  }
  //success{
    // runs when the pipeline is succesfull
  //}
  //failure{
    //runs when the pipeline is a failure. 
  //}
}
