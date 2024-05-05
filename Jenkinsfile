//CODE_CHANGES = getGitChanges()
pipeline {

  // run with next available agent
  agent any
  tools {
    maven 'Maven'

  }

  environment {
    NEW_VERSION = '1.3.0'
    SERVER_CREDENTIALS = credentials('server-credentials')
  }

  parameters {
    //string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
    choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
    booleanParam(name: 'executeTests', defaultValue: true, description: '')
  }

  stages {

    stage("build") {
      steps {
        echo 'building the application...'
        //echo "building version ${NEW_VERSION}"
        //sh "mvn install"
      }
    }
    stage("test") {
      // conditional example:
      // when {
      //   expression {
      //     // Jenkins env variable
      //     BRANCH_NAME == 'dev' || CODE_CHANGES == true
      //   }
      // }
      when {
        expression {
          params.executeTests
        }
      }
      steps {
        echo 'testing the application...'
      }
    }
    stage("deploy") {
      steps {
        echo 'deploying the application...'
        echo "deploying version ${params.VERSION}"
        // withCredentials([
        //   usernamePassword(credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PWD)
        // ]) {
        //     sh "some script ${USER} ${PWD}"
        // }
      }
    }
  }
  // post {
  //   always {
      
  //   }
  //   success {
      
  //   }
  //   failure {
      
  //   }
  // }
}
