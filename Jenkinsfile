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
                        sh "ansible-playbook -e 'ansible_become_password=onepiece007' ansible/build.yml -i ansible/inventory/host.yml"
                    }
                }
            }
        }
}