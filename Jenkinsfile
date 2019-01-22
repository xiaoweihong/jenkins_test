pipeline {
    agent {
        label 'go'
    }
    stages {
        stage('UnitTest') {
            steps {
                script {
                    if( sh(script: 'docker run --rm -v $(pwd):/go/src/gowebdemo -w /go/src/gowebdemo golang:1.11.0 /bin/bash "rununittest.sh"', returnStatus: true ) != 0 ){
                       currentBuild.result = 'FAILURE'
                    }
                }
                junit '*.xml'
                script {
                    if( currentBuild.result == 'FAILURE' ) {
                       sh(script: "echo unit test failed, please fix the errors.")
                       sh "exit 1"
                    }
                }
            }
        }
        stage('Build') {
            steps {
                sh 'bash buildapp.sh'
            }
        }
        stage('Deploy') {
            steps {
                sh 'bash deployapp.sh'
            }
        }
    }

}