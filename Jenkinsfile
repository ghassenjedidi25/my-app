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
                        sh "ansible-playbook ansible/build.yml -e ansible-become-pass=onepiece007 -i ansible/inventory/host.ini "
                    }
                }
            }
        }
}