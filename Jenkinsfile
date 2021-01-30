/*
 * Standardized Jenkinsfile for Ansible Role
 */

pipeline {
    agent {
        docker {
            image 'zollo/ansible-ci:latest'
            args '--network host -u root:root -v $HOME/.cache:/root/.cache'
        }
    }

    environment {
        VCENTER = credentials('infra-vcenter-zollo-vca01')
        ANSIBLE_HOST_KEY_CHECKING = "False"
    }

    stages {

        stage ('Configure Molecule Drivers') {
            steps {
                checkout(
                    [
                        $class: 'GitSCM',
                        branches: [[name: '*/master']],
                        doGenerateSubmoduleConfigurations: false,
                        extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'ansible-ci-win']],
                        submoduleCfg: [],
                        userRemoteConfigs: [[credentialsId: 'github-ssh-joezollo',
                            url: 'git@github.com:zollo/ansible-ci-windows.git']
                        ]
                    ]
                )

            }
        }

        stage ('Molecule Test') {
            steps {
                sh "mol test --all"
            }
        }
    }
}