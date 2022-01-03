self contained project to
- setup directory to use custom ansible path
- initialize project, with directories, virtualenv, and git commit auto-functionality
- create consul backed vault cluster with docker compose
- template out a file with consul-template
- update vault secret and see changes reflect in templated file


How to use:
1. have ansible (ansible-playbook) installed to your path
2. cd into project directory
  (./consul-template-demo)
3. setup local ansible
  ansible-playbook setup_ansible.yml
4. setup project
  ansible-playbook setup_application.yml
5. assume venv and change to ansible directory
  source ./start.sh
6. create vault cluster
  (from the ansible directory)
  ansible-playbook docker_provisioners/local_consul_vault.yml
7. create consul template. This will run the final command as a process
  ansible-playbook consul_template/consul-template-test.yml
8. check the output of test.txt created in step 7
9. in a new window, because consul-template is running as process from step 7,
  cd to project directory
  source ./start.sh
  ansible-playbook utilities/create_vault_service.yml
1-. check the output of test.txt created in step 7 and updated from the separate vault update in step 8
