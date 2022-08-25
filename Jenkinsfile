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
                docker build -t nadiasfs/cloud_kelompok2:v1 .
                '''
            }
        }
        stage("Push Image"){
            steps{
                sh '''
                set +x
                docker login --username=nadiasfs --password=$kelompok2
                set -x
                docker push nadiasfs/cloud_kelompok2:v1
                '''
            }
        }
    }
}

