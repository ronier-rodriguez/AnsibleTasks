Readme file:

Creator:	Ronier A Rodríguez V

requeriments:
Both these tasks were defined on a Vagrant machine with CentOS Linux release 7.6.1810 (Core). The vagrantfile was included for simplicity, but it is not required.
The hosts file for this test was also included. Please note that the ansible ssh port has been changed to 2222 while I was running the playbooks.

MariaDB instalation:
For this test I defined two Ansible roles. One for all the instalation of Docker, and one for the instalation and setup of the mariaDB.
To obfuscate the credentials, Ansible vault was used.

This task can be ran as:
ansible-playbook -i hosts Ansible/task1.yaml --vault-password-file=.vaultfile


Jenkins instalation:
For this task I defined an Ansible role called jenkins-pipeline. This role install Jenkins through Docker, uses a groovy script to set the initial
admin user (user: admin, pass: admin). And preinstall the usual plugins + job-dsl and python interpreter. 

To test the proposed solution, first run the playbook:
ansible-playbook -i hosts Ansible/task2.yaml

go to http://127.0.0.1:8080. Log in as admin:admin, skip the "getting started" section (because the plugins has been instaled already).
Create a Pipeline job and use "Pipeline script from SCM" "Git" and the public repo:
https://github.com/ronier-rodriguez/seeddsl.git
Run this job and this will generate the "DSL-generated-job" Job on Jenkins.

(Note: the "ERROR: script not yet approved for use" will be present as the DSL script is being included for the first time.
To disable it, just go to: "Manage Jenkins" -> "In-process Script Approval", and accept the script)

This job can be executed and will ran the "python-ip-script" Repo without problems.
