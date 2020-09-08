So you can make different groups in hosts.ini using the already set pattern.
In order to bypass typing the ssh key passprahse you need to use ssh agent forwarding (e.g- eval "$(ssh-agent -s)" + ssh-add ~/.ssh/id_rsa)
If you want to run a command against a particular grp of hosts do (ansible -i hosts.ini -m ping speeches) where speeches would be host grp defined in hosts.ini file
Test if the hosts are visible (ansible -i hosts.ini -m ping hosts) This should return a success message.
If you want to run a playbook against a particular grp of hosts do (sudo ansible-playbook -i hosts.ini -l speeches ansible-playbook.yml) where -l speeches would be the hosts grp defined in hosts.ini file
