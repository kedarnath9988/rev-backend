pipeline {
    agent {
        label 'backend-01'
    }
    options {
        timeout(time:30, units:'MINUTES')
        diableconcarentbuils()
        ansicolour('xterm')
    }

    environment {
        def app_version = ''
    }

    satges {
        stage('get_varsion'){
            script{
                def get_varsion = readJSON file: 'package.json'
                app_version = get_varsion.version 
                echo "appversion is $app_version"
                }
             }
            satge('downlode_dep'){
                input{

                }
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