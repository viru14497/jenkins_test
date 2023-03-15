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
         stage('Print Last Commit Branch Name') {
        when {
            expression {
            GIT_BRANCH = 'origin/' + sh(returnStdout: true, script: 'git reflog show --all | grep "$(git rev-parse HEAD | cut -c1-7)" | grep -o "refs/.*@" | grep -o /[a-zA-Z.0-9]*@|tail -c +2 | head -c -2').trim()
            return (GIT_BRANCH == 'origin/master')
        }
        steps {
                sh 'echo "Its $GIT_BRANCH"'
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
