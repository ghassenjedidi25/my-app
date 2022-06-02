pipeline {
    agent any
    tools {nodejs "node"}
        stages {
            stage('Pull') {
                steps{
                    script{
                        checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                            userRemoteConfigs: [[
                                credentialsId:'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',
                                url: 'https://github.com/ghassenjedidi25/my-app'
                            ]]])
                    }
                }
            }
            stage('build') {
                steps{
                    script{
                        sh "npm install"
                        sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.ini "
                    }
                }
            }
            stage ('docker') {
                steps{
                    sh "pip install docker"
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.ini"
                }
            }
        }
}