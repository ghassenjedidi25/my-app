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
                    sh "pip3 install docker"
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.ini"
                }
            }
        }
}