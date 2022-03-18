
node{
    stage('Clone git') {
        checkout scm
    }
    stage('Prerequis'){
         apk add ansible sshpass
         echo '192.168.88.132 app-salaire.mohamed.form' > /etc/hosts
         rm -rf /root/ssh
         ssh-keygen -q -t rsa -N '' -f ~/ssh/id_rsa
         sshpass -p 'centos' ssh-copy-id -o stricthostkeychecking=no root@app-salaire.mohamed.form
    }
    stage('Ansible') {
      ansiblePlaybook (
          colorized: true,
          playbook: 'playbook.yaml',
          inventory: 'hosts.yaml'
      )
    }
}
