properties([pipelineTriggers([githubPush()])])

pipeline {
    /* specify nodes for executing */
    agent any
    
    stages {
        /* checkout repo */
        stage('Checkout SCM') {
            steps {
                checkout([
                 $class: 'GitSCM',
                 branches: [[name: 'master']],
                 userRemoteConfigs: [[
                    url: 'https://github.com/gomesar9/integration.git',
                    credentialsId: '',
                 ]]
                ])
            }
        }
        
        stage('Show Info') {
            steps {
                echo 'Branch: ' + env.GIT_BRANCH
                echo 'Author: ' + sh(returnStdout: true, script: "git --no-pager show -s --format='%an'").trim()
            }
        }

        stage('Do the deployment') {
            steps {
                echo ">> Run deploy applications."
            }
        }
    }
    

    /* Cleanup workspace */
    post {
       always {
           deleteDir()
       }
   }
}
