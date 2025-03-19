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
        stage ('get_version') {
        steps{
            script {
              def   packege_ver = readJSON file: 'package.json'
              app_version = packege_ver.version
              echo "app version is $app_version"
            }
            }
        }
        stage ('install dep') {
            steps {
                sh """
                npm install 
                ls -ltr 
                """
            }
        }
        stage ('build file ') {
            steps {
                sh """
                
                zip -q -r backend-${app_version}.zip *  -x Jenkinsfile -x backend-${app_version}.zip
                ls -ltr

                """
            }
        }
        stage ('Nexus Artifact Uploader') {
            steps {
                script {                  
                    sh '
                    '''
                }
                nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'https',
                    nexusUrl: '',
                    groupId: 'expense',
                    version: "$app_version",
                    credentialsId: "nexus3",
                    repository: 'maven-releases',
                    artifacts: [
                        [artifactId: 'backend',
                         classifier: '',
                         file: 'src/main/resources/spots/spots-$VERSION.zip',
                         type: 'zip']
                    ]
                 )
            }
        }
    }
    post {
        always {
            echo 'always existed'
            
        }
        success {
            echo "pipeline successful"
        }
    }

}
