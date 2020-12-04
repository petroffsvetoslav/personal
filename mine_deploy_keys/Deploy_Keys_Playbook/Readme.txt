hosts.ini file is the inventory where hostnames/ips, groups and details to login those are specified.

ansible.cfg is the configuration files, where currently the check for known_hosts is disabled, so that the prompt doesn't stop
the playbook execution.

deploy-keys.yml file is the actual playbook where the user to be updated is specified (or to be created if a new user is needed),
location of the keys to provision is specified and the user is then added to the sudoers file. Note: this also works with users
that already exist and are already in the sudo group so it doesn't break anything, but if the user isn't existing or not in the sudoers 
it also executes without issues.

keys folder contains public keys for distribution.

key on person's side must be in his /home/user/.ssh dir and in the id_rsa/id_rsa.pub format and in the /keys file on the ansible master you can touch a new file
and rename it accordingly.

execute playbook with:

ansible-playbook --inventory-file=hosts.ini deploy-keys.yml

execute when you want to add new keys to the user/server and it will only add new entries (and not add existing keys a second time).