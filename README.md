This role deploys PostgreSQL 12.5 in two nodes in a master-slave configuration.

Assumption
The two nodes must be up an running. Alternatively, two VMs can be brought up with Vagrant, using the Vagrantfile provided at the root of the repo. The VMs have two network interfaces:
public: It's the interface for outside communication (ssh, postgresql clients access, etc). It has a static IP in 192.168.98.x network. replication: It's the interface for replication traffic between the nodes. It has a static IP in 192.168.99.x network.

Note: The Ansible role that will provision PostgreSQL to the VMs can be cofigured with different networks for the two interfaces, therefore the IP addresses in Vagrantfile are an example. The IPs can even be dynamic, but we choose to define them explicitly for our purpose.

Virtualbox must be installed and running when bringing up the VMs with vagrant up.
Files & Directories
A playbook to trigger the role, setup_pgsql.yml is provided.

A static Ansible inventory file, inventory.txt is provided. It has static configuration for the two VMs in two groups, pgmaster and pgslave. An ssh key insecure_private_key is specified in the inventory and installed in the VMs by Vagrant.

Note: In a production deployment the inventory would be created dynamically, if needed by the infrastructure. Again, it's statically set here for our purpose.

The Ansible role itself, role-postgresql. In defaults/main.yml there are a few variables defined, that can be overriden if necessary, e.g. by defining variable values in the playbook. Just to note here that we can define what our public and replication networks are, depending on the IPs we used in the VMs:
public_network: "192.168.98"
replication_network: "192.168.99"
How to run the role
Start Virtualbox, place Vagrantfile in a directory of your workstation and bring up the VMs running vagrant up from this directory.

Save role-postgresql, inventory.txt and insecure_private_key in a directory of your workstation. Make sure the key file has properly restricted permissions (600).

Run the playbook with ansible-playbook -i inventory.txt setup_pgsql.yml