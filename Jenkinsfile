pipeline{
    agent any
    stages{
        stage("SCM Checkout"){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CleanBeforeCheckout', deleteUntrackedNestedRepositories: true]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-login', url: 'https://github.com/Dominggus11/dockerfile']]])
            }
        }
        stage("Create Image"){
            steps{
                sh '''
                docker build -t roymalau/rdam_jenkins:v1 .
                '''
            }
        }
        stage("Push Image"){
            steps{
                sh '''
                set +x
                docker login --username=roymalau --password=$rdam
                set -x
                docker push roymalau/rdam_jenkins:v1
                '''
            }
        }
    }
}

