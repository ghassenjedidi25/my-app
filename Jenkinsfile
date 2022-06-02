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
                    sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.ini"
                }
            }
            stage ('push to docker registry') {
                steps{
                    sh "ansible-playbook ansible/docker-registry.yml -i ansible/inventory/host.ini"
                }
            }
        }
}