pipeline {
    agent any
    tools {nodejs "node"}
    tools {docker "docker"}
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
        }
}