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
                        sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml -e ansible_become_pass=onepiece007"
                    }
                }
            }
        }
}