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
                retry(3) {
                    sh 'ping www.baidu.com'
                }
                timeout(time: 3, unit:'MINUTES'){
                    sh './health-check'   
                    sh 'sleep 1'
                }
            }
        }
        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
            }
        }
        stage('Deploy') {
            steps{
                sh 'echo "make publish"'
            }
        }
        post {
            always {
                echo 'This will always run'
            }
            success {
                echo 'This will run only if successful'
            }
            failure {
                echo 'This will run only if failed'
            }
            unstable {
                echo 'This will run only if the run is marked as unstable'
            }
            changed {
                echo 'This will run only if the state of pipeline is changed'
                echo 'For example, if the Pipeline was previously failing but is now successful'
            }
        }
    }
}