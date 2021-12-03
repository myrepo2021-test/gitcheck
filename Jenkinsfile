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
        GIT_CRED = credentials('git_user')
    }
    stages {
        stage ('Git Checkout') {
            step {
                echo 'Checking Out from Git'
                git branch: params.BRANCH ,
                    credentialsId: "${GIT_CRED}" ,
                    url: "https://github.com/myrepo2021-test/gitcheck.git"

            sh 'ls -ltr'
            }
        }
        stage ('Test') {
            step {
                echo 'Checking the checked out code'
            }
        }
    }
}
