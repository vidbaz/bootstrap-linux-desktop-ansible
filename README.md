# bootstrap-linux-desktop-ansible
This are some ansible tasks to automate some packages installation on Linux (Tested on Mint and Ubuntu)

### Install virtual env with Python 3
```
sudo apt-get install python3-venv ssh sshpass -y
mkdir python_envs
cd python_envs
python3 -m venv ansible
source ~/python_envs/ansible/bin/activate
```

### Install ansible in the virtual env
```
pip install wheel
pip install ansible
ansible --version
```

### Example: Playbook Execution
```
#Activate enviroment (if not is already activated)
source ~/python_envs/ansible/bin/activate
#Ensure that you go to this repo where ansible files are located
cd bootstrap-linux-desktop-ansible 
export ANSIBLE_HOST_KEY_CHECKING=False
#Check first
ansible-playbook -i inventory main.yaml --ask-pass --ask-become-pass --check --diff
#Apply
ansible-playbook -i inventory main.yaml --ask-pass --ask-become-pass --diff
```

### Example: Execute Playbook with specify tags
```
#Activate enviroment (if not is already activated)
source ~/python_envs/ansible/bin/activate
ansible-playbook -i inventory main.yaml --ask-pass --diff --ask-become-pass --tags=config-kernel-parameters --check
```

### Example: Specific Machines

```
source ~/python_envs/ansible/bin/activate
ansible-playbook -i inventory main.yaml --ask-pass --ask-become-pass --limit=ets  -u ets --check --diff --tags=install-chrome
```


### Execute Playbook Example skipping tags
```
source ~/python_envs/ansible/bin/activate
ansible-playbook -i inventory main.yaml --ask-pass --ask-become-pass --skip-tags=install-general-packages,install-vs-code --check
```
