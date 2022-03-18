node{
    stage('Clone git') {
        checkout scm
    }
    stage('Prerequis'){
        sh apk add ansible sshpass
        sh echo '192.168.88.132 app-salaire.mohamed.form' > /etc/hosts
        sh rm -rf /root/.ssh
        sh ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa
        sh sshpass -p 'centos' ssh-copy-id -o stricthostkeychecking=no root@app-salaire.mohamed.form
    }
    stage('Ansible') {
      ansiblePlaybook (
          colorized: true,
          playbook: 'playbook.yaml',
          inventory: 'hosts.yaml'
      )
    }
}
