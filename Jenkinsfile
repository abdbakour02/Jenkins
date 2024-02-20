CODE_CHANGES = getGitChanges()

pipeline {
  agent any
  environment {
    NEW_VERSION = '1.3.0'
    SERVER_CREDENTIALS = credentials('Server-cred')
  }
  tools {
    maven 'maven3'
    jdk 'jdk17'
  }
  parameters {
    choice(name: 'VERSION', choices: ['1.2.0', '1.2.1','1.3.0'], description: '')
    booleanParam(name: 'executeTests', defaultValue: true, description: '')
  }
  
  stages {
  
    stage('Build'){
      when {
        expression {
          BRANCH_NAME == 'feature-one' && CODE_CHANGES == true
        }
      }
      steps {
        echo 'building the application..'
        echo "buildling version ${NEW_VERSION}"
      }
    }
    
    stage('Test'){
      when {
        expression {
          param.executeTests  // param.executeTest = true
        }
      }
      steps {
        echo 'testing the application..'
        withCredentials([
          usernamePassword(credentials:'User-cred', usernameVariable: User, passwordVariable: PWD)
          ]) {
            sh "some script ${User} ${PWD}"
        }                     
      }
    }
    
    stage('Deploy'){
      steps {
        echo 'deploying the application..'
        echo "deploying with ${Server_CREDENTIALS}"
        sh "${SERVER_CREDENTIALS}"
        echo "deploying version ${param.VERSION}"
      }
     }
  }

    post {
    always {
      echo 'this is post section executed always or when success or failure'
    }
  }
}
