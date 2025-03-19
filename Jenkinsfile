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
        stage('Dev') {
            steps {
                sh """
                echo this is build
                """
            }
        }
        stage('QA') {
            steps {
                sh """
                echo this is QA
                """
            }
        }
        stage('UAT') {
            steps {
                sh """
                echo this is UAT
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
