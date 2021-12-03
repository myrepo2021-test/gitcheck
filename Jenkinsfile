pipeline{
    agent any
    /* {
        node {
            label 'docker'

        }
    } */
    parameters {
        choice(name: 'VERSION', choices:['1','1.1','1.2','1.3'], description: 'To Select Version')
        choice(name: 'BRANCH', choices:['master', 'dev','prod'], description: 'Select Branch to Build')
    }
    environment {
        // DOCKER_URL = https://hub.docker.com/repository/docker/renuka2021/dockerrepo
        // GIT_URL = https://github.com/myrepo2021-test/gitcheck.git
        // GIT_CRED = credentials('git_user')
        CHECK = BRANCH
    }
    stages {
        stage ('Git Checkout') {
            steps {
                echo 'Checking Out from Git'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '7da824c6-7cc1-4681-bf28-5b7991b591e7', url: 'https://github.com/myrepo2021-test/gitcheck.git']]])
                sh 'ls -ltr'
            }
        }
        stage ('Test') {
            steps {
                echo 'Checking the checked out code'
            }
        }
    }
}
