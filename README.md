# Documentation and soureces for the "Learn DevOps - continuously deliver better software" Udemy course by Edward Viaene

## Part 1 : Ansible
Instal Vagrant & VirtualBox 

Start test VM's for Ansible server and Test-Webserver by running :
> cd ansible/ \
> vagrant up ansible \
> vagrant up webserver

Install ansible :
>vagrant ssh ansible \
>sudo apt-get install ansible (TODO: provision softwahre installation with the Vagrant, TODO2 Update Ansible to the newest version)

Generate ssh key on Ansible machine:
>ssh-keygen

Leave default filename and no passphrase. Copy private key by
>cat /home/vagrant/.ssh/id_rsa.pub

and copy console output in the buffer. Exit Ansible machine and login into test webserver and save public key there:
>vagrant ssh webserver
>echo 'content of the ssh pub key' >/root/.ssh/authorized_keys

setup inventory file on the ansible machine (TODO: mount project forlder into the ansible)
> nano hosts

[webservers] \
192.168.0.2 

Enable ssh agent (TODO : add to .profile by Vargant provision):
>ssh-agent bash \
>ssh-add .ssh/id_rsa

Test your setup vith the ansible ping: 
>ansible -i hosts -u root -m ping all

Run nginx install with the nginx.yml script.
>ansible-playbook -i hosts -u root nginx.yml

Run nginx install with the configuration template
>ansible-playbook -i hosts -u root nginx.v2.yml