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
                        sh "ansible-playbook ansible/build.yml -e ansible_become_pass=onepiece007 -i ansible/inventory/host.ini "
                    }
                }
            }
        }
}