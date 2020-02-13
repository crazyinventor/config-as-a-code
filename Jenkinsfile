node {
    checkout scm

    stage('Decryption') {
        withCredentials([file(credentialsId: 'vault_pass', variable: 'vault-pass-file')]) {
            sh "cp \$vault-pass-file ./vault_pass.txt"
        }
    }

    stage('Provision') {
        sh 'ansible-playbook provision.yml --vault-password-file ./vault_pass.txt'
    }

    stage('Deployment') {
        sh 'ansible-playbook deployment.yml --vault-password-file ./vault_pass.txt'
    }
}
