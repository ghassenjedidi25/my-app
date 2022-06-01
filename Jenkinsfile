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
                        sh "ansible-playbook ansible/build.yml -e ansible_sudo_pass='azerty' -i ansible/inventory/host.ini"
                    }
                }
            }
        }
}