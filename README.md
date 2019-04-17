# Oracle_CDBnPDB_19c
# Create Oracle container database and pluggable database

Note: Please modify all necessary configuration files based on your own environment.For Example, one can modify dbca reposity file to create CDB and PDB at the same time and no need to run PDB create role.

This repository is for the Creating and configuring a  multitenant container database (CDB) includes tasks such as creating the CDB, and then Pluggable database (PDB) using Oracle Database 19c 64-bit on Oracle Linux.

Current Setup for this repository: 
OS: OEL 7.5 
Ansible: ansible 2.7.6
Oracle RDBMS Software Version: 19.2 

Prior Article for this to follow - 

DevOps Series: Automate Oracle 19c RDBMS Installations with Ansible [GITHUB]
https://medium.com/oracledevs/devops-series-automate-oracle-19c-rdbms-installations-with-ansible-github-43cfdf344a4a

Major Steps for this playbook role: 
   1 :Create and configure silent listener config file
   2 :Create silent database install file 
   3 :Create a Container Database
   4 :Enable database archivelog
   5 :Create a Pluggable Database with local undo  
   6 :Open pluggable database in normal mode
   7 :Execute tns update for PDB database 
    
Summary commands: 

1. Clone this repository:
git clone https://github.com/asiandevs/Oracle_CDBnPDB_19c
   
2. Define variables as per your setup or requirements [ Modify main.yml file under vars directory ]

3. Configure an Ansible inventory file (example as below) 
[root@oel75 ansible]# cat ansible.cfg | grep inventory
inventory = ./inventory
[root@oel75 ansible]# cat inventory
[ora-x1]
192.168.56.102
[ora-x2]
192.168.56.103
[dbservers]
192.168.56.102
192.168.56.103

4. Run the playbook role "cdb_pdb_create.yml"
ansible-playbook cdb_pdb_create.yml [ with options for testing, use --check / --diff / --step / -vvv ]
