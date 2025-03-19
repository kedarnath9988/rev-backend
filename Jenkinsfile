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
        stage('get_version') {
            script {
              def   packege_ver = readJSON file: 'package.json'
              app_version = packege_ver.version
              echo "app version is $app_version"
            }
        }
        stage('install dep') {
            steps {
                sh """
                npm install 
                ls -ltr 
                """
            }
        }
        stage('build file ') {
            steps {
                sh """
                
                zip -r backend-${app_version}.zip -x Jenkinsfile -x backend-${app_version}.zip

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
