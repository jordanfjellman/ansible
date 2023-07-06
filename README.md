# Ansible

## Prerequisites

Before we can install Ansible, make sure the XCode command line tools are
installed:

```shell
xcode-select --install
```

And we'll need to install [Homebrew](https://brew.sh/):

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Installation on OSX

The [preferred way](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-macos)
to install Ansible on OSX is [with PIP](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-with-pip).
However, since OSX does not come with Python 3 natively, we would need to
install Python 3 before we could use PIP. We could use Homebrew to upgrade to
Python 3, but at this point we might as well install Ansible directly.

```shell
brew install ansible
```

Now that Ansible is installed, we need to include the _community.general_
"galaxy" in order to setup the [Homebrew plugin](https://docs.ansible.com/ansible/latest/collections/community/general/homebrew_module.html)

```shell
ansible-galaxy collection install community.general
```

## Run Initial Machine Setup

1. Setup Dotfiles
  ```shell
    ansible-playbook --ask-vault-pass --tags dotfiles local.yml
  ```
1. Run the remaining initial install scripts
  ```shell
    ansible-playbook --tags <tag> local.yml
  ```

## Resources

- [ThePrimagen](https://github.com/ThePrimeagen/ansible)

