Ansible Role: vim
=========

pip install cryptography==3.4.7

![ScreenShot](https://raw.github.com/DevopsishFriends/DevopsishVim/master/screenshot.png)

This role can:

- install all the needed software
- install vimrc file and plugins

Requirements
------------

The target hosts need to have `apt` to install deb packages.

Role Variables
--------------

Refer to `defaults/main.yml`

Dependencies
------------

None

Example Playbook
----------------

    - name: test role
      hosts: vagrant
      roles:
        - role: vim
          config_src: ~/.vim/vimrc

Also refer to `tests/test.yml`

DIY On Your Local Ubuntu
-----------------------

```
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
sudo apt install git
mkdir vim_DIY
cd vim_DIY
git clone https://github.com/pesarkhobeee/DevopsishLaptop
cat >> DIY.yml <<EOF
- name: DevopsishLaptop role
  hosts: 127.0.0.1
  connection: local
  ignore_errors: yes
  roles:
    - role: DevopsishLaptop
EOF
```

If you want to just have vimrc and all plugins on your pre-installed vim :

```
ansible-playbook -t vimrc -e ansible_python_interpreter=$(which python3)  --ask-become-pass DIY.yml
vim -c ":PlugInstall" 
```

But if you also like to compile and install Vim from the source run this command instead of the previous one:

```
ansible-playbook -e ansible_python_interpreter=$(which python3)  --ask-become-pass DIY.yml
```


License
-------

MIT

Authors Information
------------------

* https://github.com/guoqiao
* https://github.com/pesarkhobeee

