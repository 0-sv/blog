---
title: "Ansible Common Errors"
date: 2020-04-05T18:05:33+07:00
draft: true
tags:
  - ansible
---
When browsing any social media platform, I always see a ton of questions for Ansible that are related to execution. It must be very frustrating to become stuck with one of the most popular configuration management tools in the early stages. I know I was; my original task as Systems Engineer was configuration management with Ansible, and I believe I spent 3 months out of 6 trying to get Ansible to work. 

After seeing the common patterns in debugging it does become your favorite toolkit though, as it provides a very fancy wrapper around Bash. Whenever you have a new project in sight, there's probably someone before you who posted their Ansible Role on Ansible Galaxy, making it possible to start your project with a blueprint for whatever needs to be done. Moreover, you won't lose sleep over Bash scripts that go awry when you can CI/CD your Ansible repositories with Ansible Molecule.

Anyway, I've answered Ansible questions here and there; to that end, here's a list of common errors and ways to think about it. I will extend this list whenever I see fit. If you have any suggestions, there's also the possibility of a pull request on the Github page for this website.

# "No module named ..."

I've copied one of the definitions of the k8s_info module which uses the same interface as the k8s module. It throws the following error:

    TASK [ansible-install-helm : Get a list of all pods from any namespace] ********
    ImportError: No module named kubernetes

This error is expected. We're just gonna assume that whatever host we run this Ansible role on, we should expect that the kubernetes and openshift Python modules are available. We can reproduce this error by opening Python3 and import kubernetes and/or openshift:

    (all) sv ansible-install-helm $ python3
    Python 3.8.2 (default, Feb 29 2020, 17:03:31) 
    [GCC 9.2.0] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import kubernetes
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    ModuleNotFoundError: No module named 'kubernetes'

Since our host is localhost, we can solve this problem by installing the kubernetes and openshift modules with a package manager like pip:

    pip install openshift kubernetes

# Ansible Output Is Not Clearly Formatted**

I'm sure you've experienced the Ansible error output to be completely unreadable without formatting. We can solve for that problem by configuring the 'stdout_callback' option. For human-readable output, it should equal 'yaml'. Append this to either /etc/ansible/ansible.cfg for regular Playbook execution, or as provisioner.config_options.defaults.stdout_callback in {role_path}/molecule/default/molecule.yml. 

    echo "stdout_callback = yaml" | sudo tee -a /etc/ansible/ansible.cfg

    # {role_path}/molecule/default/molecule.yml
    provisioner:
      name: ansible
      config_options:
        defaults:
          stdout_callback: yaml
