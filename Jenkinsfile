pipeline {
    agent any
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
                        sh "ansible-playbook --ask-become-pass ansible/build.yml -i ansible/inventory/host.yml"
                    }
                }
            }
        }
}