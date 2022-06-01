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
                        sh "ansible-playbook ansible/build.yml -e 'ansible_become_password=onepiece007' -i ansible/inventory/host.yml"
                    }
                }
            }
        }
}