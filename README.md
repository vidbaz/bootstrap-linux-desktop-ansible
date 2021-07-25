# bootstrap-linux-desktop-ansible
This are some ansible tasks to automate some packages installation on Linux (Tested on Mint and Ubuntu)

### Install virtual env with Python 3

```
sudo apt-get install python3-venv
sudo mkdir python_envs
cd python_envs
python3 -m venv ansible
source ansible/bin/activate
```

### Execute Playbook Example

```
export ANSIBLE_HOST_KEY_CHECKING=False
$ ansible-playbook -i inventory main.yaml --ask-pass --ask-become-pass
```