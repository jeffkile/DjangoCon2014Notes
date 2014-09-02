Development with Ansible and VMs
Jeff Schenck
slides: bit.ly/dev-ansible-vm


1. Better dev environment
Standardized
Repeatable
Isolated
As similar to production as possible
Use your dev tools
Sharable

2. Environment Tools
Good things to keep using:
    PIP
    Virtualenv
VM
    Virtual box
    Vagrant - CLIs for Virtual Box

    VM Setup:
    ```
    vagrant init hashicorp/precise64
    vagrant up
    vagrant ssh
    ```

    Vagrant setup script:
    ```
    Vagrant::configure("2") do |config|
        config.vm.box = "hashicorp/precise64
        config.vm.hostname = "foo"
        config.vim.network "private_network", ip: "10.0.0.100"

        config.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible/foo.yml
        end
    end
    ```

3. Configuration Management
Define System Setup
Written in code
Documented and versioned

Competing setup tools:
chef, puppet, ansible, saltstack, bash

Ansible example:
(think of it as a list of steps each step given a name)
```
- name: standard python system packages
    // Use apt package manager to install packages
    apt: pkg={{ item }} state= installed
    // Replace {{ item }} with each thing listed below
    with items:
        - python
        - python-dev
        - python-pip
- name: bootstrap pip and virtualenv
    pip: name={{ item.name }} version={{ item.version }}
    with_items:
        - { pip: pip, version: 1.4.1 }
        - { name: virtualenv, version: 1.10.1 }
    sudo: yes
- name: install requirements.txt
    pip: requirements=/vagrant/requirements.txt virtulenv=/var/venv
    sudo: yes
-name: source virtualenv in .bashrc
    // Make sure each line is the .bashrc file
    lineinfile: dest=/home/vagrant/.bashrc line="{{ item }}"
    with_items:
        - source /var/activate
        - cd bar
```


4. Wrap Up
Seting up a new developer:
    Install Virtualbox and Vagrant
    `git clone repository_with_vagrant_script`
    `vagrant up`




