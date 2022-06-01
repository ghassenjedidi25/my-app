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
                        sh "ansible-playbook ansible/build.yml -e ansible_sudo_pass='onepiece007' -i ansible/inventory/host.ini"
                    }
                }
            }
        }
}