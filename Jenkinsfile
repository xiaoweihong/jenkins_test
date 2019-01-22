pipeline {
    agent {
        label 'go'
    }
    stages {

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
    post {

    }
}