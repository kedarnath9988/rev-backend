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
      /stage('get_version'){
            script{
                def get_varsion = readJSON file: 'package.json'
                app_version = get_varsion.version 
                echo "appversion is $app_version"
                }
             }
            stage('downlode dep'){
                steps{
                    sh """
                    npm install 
                    ls -ltr 
                    echo "check the node_module file is crated or not"
                    """
                }

            }
           stage('build'){
                sh """
                zip -r backend-$app_version.zip -x Jenkinsfile -x backend-$app_version.zip

                """
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
