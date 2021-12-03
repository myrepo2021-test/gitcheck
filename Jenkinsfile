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
        // DOCKER_URL = 'https://hub.docker.com/repository/docker/renuka2021/dockerrepo'
         GIT_URL = 'https://github.com/myrepo2021-test/gitcheck.git'
        DOCKER_LOGIN =credentials('DockerLogin')
        // GIT_CRED = credentials('git_user')
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
        stage ('Docker') {
            steps {
                echo 'Docker Login'  
                withDockerRegistry([ credentialsId: "5bff77df-6b9e-4345-9241-d99fdc4218c0", url: "" ]) {
                    echo 'Logging into Docker'
                    sh 'docker login renuka2021/sample -u ${USER} -p ${PWD}'
                    sh 'docker pull renuka2021/sample:39'
                    sh 'docker ps'
                }
                
            }
        }
    }
}
