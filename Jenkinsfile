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
                script{
                    sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml"
                }
            }
        }
}