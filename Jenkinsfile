pipeline {
    agent {
        label 'master' /* 执行节点 */
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        stage('Deploy - Staging') {
            steps {
                echo './deploy staging'
                echo './run-smoke-tests'
            }
        }
        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }
        stage('Deploy - Production') {
            steps {
                echo './deploy production'
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'success'
        }
        unstable {
            echo 'unstable'
        }
        failure {
            echo 'failure'
        }
        changed {
            echo 'Things were different before...'
        }
    }
}