pipeline {
    agent {
        label 'backend-01'
    }
    options {
        timeout(time:30, unit:'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }

    environment {
        def app_version = ''
    }

    stages {
      stage("hello"){
        steps{
            sh """
            echo this is hello 
            """
        }
      }

      stage("hello"){
        steps{
            sh """
            echo this is hello 
            """
        }
      }

      stage("hello"){
        steps{
            sh """
            echo this is hello 
            """
        }
      }

    }
    post {
        always {
            echo 'always existed'
            deleteDir()
        }
        success {
            echo "pipeline successful"
        }
    }

}
