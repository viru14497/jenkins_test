pipeline {
    agent any

    stages {
        stage('Checkout: Code') {
          steps {
            checkout([$class: 'GitSCM',
            branches: [[name: '*/master']],
            doGenerateSubmoduleConfigurations: false,
            submoduleCfg: [],
            userRemoteConfigs: [[credentialsId: '9f504356-8a4b-4cb3-a1e8-f59cb27f4ca2', url: 'https://github.com/viru14497/jenkins_test.git']]
            ])
           }
         }
        stage('Print Branch Name') {
            steps {
                sh 'echo "Building branch $BRANCH_NAME"'
            }
        }
        stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                sh 'echo "Deploying to production..."'
            }
        }
    }
}
