# Internet-in-a-Box (IIAB) Development Mode

This repository provides a quick setup of Internet-in-a-Box (IIAB) development environment using Vagrant. You will
need a computer with virtualization enabled and git, Vagrant (2.0 or later) and VirtualBox installed.

## Requirements

 * [git](https://git-scm.com/)
 * [Vagrant (2.0 or later)](https://www.vagrantup.com/)
 * [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
 * Editor ([Atom](www.atom.io), Emacs, Vi etc)
 * [Ansible](http://www.ansible.com/)
 * [Ansible-lint](https://github.com/willthames/ansible-lint) and [Ansible-review)[https://github.com/willthames/ansible-review] tools


## Usage
1. Check out this repository and its submodules on to your development machine.
`git clone --recursive https://github.com/arky/iiab-dev-mode.git`

2. Change directory into 'iiab-dev-mode' with `cd iiab-dev-mode`. You can update all the submodules to latest master using `git submodule foreach git pull origin master`

3. Setup a vagrant machine with `vagrant up` and provision it with `vagrant provision`. Please select the available bridge network interface (wlan0 or eth0) that connects your host machine to the Internet.

4. You can now connect to your vagrant machine with `vagrant ssh`. All your local development files available as shared folder in `/opt/iiab` directory.

5. You can setup IIAB from the Ansible Playbooks following the [installation wiki page.](https://github.com/iiab/iiab/wiki/IIAB-Installation)

          cd /opt/iiab/iiab/scripts/
          ./ansible

          cd /opt/iiab/iiab/
          ./runansible

          cd /opt/iiab/iiab-admin-console/
          ./install

          cd /opt/iiab/iiab-menu/
          ./cp-menus
6. Hack away! You can commit your local changes and send pull request to IIAB project by setting a default git remote push setting with `cd <repo> && git remote set-url --push origin git@github.com:<your_username>/<your_forked_iiab_repo_name>.git`.  Learn more by reading this [blog post](http://blog.yuriy.tymch.uk/2012/05/different-git-push-pullfetch-urls.html) and [Working with Remotes in Pro Git Book](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes)

7. Once you are done, you can stop your vagrant machine with `vagrant halt` or remove it completely with `vagrant destroy`.
