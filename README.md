# LAMP Ansible with mariadb, php7 and php-fpm

A basic set of playbooks to provision ubuntu/debian with Apache, MariaDb, Php7 with FPM

The code is accompanied with a Vagrant file configuration.
Dockerize is pending, any contribution is welcome.


## Configuration

You can configure Apache, Php, MariaDb and demo vhost by modifying the values set up into the yml files in group_vars/demo folder:

- apache2.yml
- mariadb.yml
- php7-fpm.yml
- contents.yml


## Roles

- apache2
- mariadb
- ntp
- php7-fpm
- xdebug
- contents


## Vagrant

There is a full working Vagrant configuration that allows creating and provisioning a full virtual machine


### Installation:

    - vagrant up (optional)
    - ./playbooks.yml ( OR: ansible-playbook --private-key=~/.vagrant.d/insecure_private_key -u vagrant -i ./inventories/demo playbook.yml )

    If you have any problems when running sudo ./ansible.yml, check your ~/.ssh/known_hosts and remove any entry referemcing 127.0.0.1

    Right Installation can be checked by browsing: http://localhost:10080
    Adding demo.intranet with the ip 192.168.50.100 in the OS hosts file, demo site can be checked by accessing: http://demo.intranet

**Characteristics:**

Note that you can change the default folder for Virtual Machines generated by VirtualBox from VirtualBoxMenu => Preferences => General.


- Virtual Machine Name

    - vb.name = "vagrant_lamp"
     
- Vagrant hard drive custom size: 256Gb set up. This value can modified by changing the argument
 
    - vb.customize [ '--size', NEW_SIZE_IN_MB * 1024 ]

- Private Network Ip
    
    - vagrant_lamp.vm.network "private_network", ip: "192.168.10.100"

- Hard Drive File Name
    
    - file_to_disk: Is saved with the name 'disk2.vdi' in the same folder where the VirtualMachine will be created.

- RAM

    - vb.customize ["modifyvm", :id, "--memory", "2048"]

- CPUS
    - vb.customize ["modifyvm", :id, "--cpus", "2"]

- Synced Folder

    - vagrant_lamp.vm.synced_folder "./www_demo", "./www_demo", :type => "nfs", mount_options: ['rw', 'vers=3', 'tcp', 'fsc']


## Docker

Pending to do.
Contributions are welcome.


## License

LAMP Ansible is released under the [MIT License](LICENSE).
