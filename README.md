# bootstrap-linux-desktop-ansible
This are some ansible tasks to automate some packages installation on Linux (Tested on Mint and Ubuntu)

### Install virtual env with Python 3
```
sudo apt-get install python3-venv ssh sshpass -y
sudo mkdir python_envs
cd python_envs
python3 -m venv ansible
source ansible/bin/activate
```

### Install ansible in the virtual env
```
pip install wheel
pip install ansible
ansible --version
```

### Execute Playbook Example
```
export ANSIBLE_HOST_KEY_CHECKING=False
$ ansible-playbook -i inventory main.yaml --ask-pass --ask-become-pass
```


### Execute Playbook Example skipping tags
```
export ANSIBLE_HOST_KEY_CHECKING=False
$ ansible-playbook -i inventory main.yaml --ask-pass --ask-become-pass --skip-tags=install-general-packages,install-vs-code --check
```
