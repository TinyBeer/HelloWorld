pipeline {
    agent any 
    stages {// 阶段
        stage('build') {// build stage 
            steps {
               sh 'echo "make"'
            }
        }
        stage('test') {// test stage
            steps{
                sh 'echo "make check"'
            }
        }
        stage('Deploy') {
            steps{
                sh 'echo "make publish"'
            }
        }
    }
}