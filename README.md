# Ansible Automation Platform with IBM HashiCorp Vault Enterprise and Terraform Enterprise

This repository contains the Ansible and Terraform based deployer for an enterprise automation demonstration environment. The environment contains the following:

- Ansible Automation Platform
  - Containerized installation, on Red Hat Enterprise Linux 9
- HashiCorp Vault Enterprise
  - on RHEL 9
- HashiCorp Terraform Enterprise
  - Containerized installation on Podman, on RHEL 9
- GitLab Community Edition (CE)

## Purpose

The purpose of this environment and deployer is to demonstrate the fully config-as-code implementation of a complete automation solution. All that is needed is for configuration to be setup in `group_vars/all.yml` based on the example provided.

## Demo deployment process

1. Create a `group_vars/all.yml` based on `group_vars/all.yml.example`.
   1. Specifically note the variables with `CHANGEME` or `example` in their values.
2. Configure your AWS credentials, and either export `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` or `AWS_PROFILE` so that Ansible has access to your access keys.
3. Execute `ansible-playbook deploy-hosts.yml`.
   1. This creates 4 AWS hosts for the software.
4. Execute `ansible-playbook install-hashi-vault.yml`.
   1. This deploys HashiCorp Vault and creates the SSL certificates for all hosts.
   2. It also creates the secrets engine and loads values into it for critical values.
5. Execute `ansible-playbook install-aap.yml`.
   1. This deploys Ansible Automation Platform and configures the credentials, projects, and jobs needed to run the environment.
6. Login to AAP using the `admin` user and the password that you specified in `group_vars/all.yml`.
7. Click on `Automation Execution` and then `Templates`.
8. Click on the rocketship icon to the right of `RH-Hashi Demo - Install install-gitlab.yml`, and monitor the installation for success.
   1. AAP will now install and configure GitLab Community Edition, and return success or failure.
9. Click on the rocketship icon to the right of `RH-Hashi Demo - Install install-terraform.yml`, and monitor the installation for success.

With that, the environment is up and running.

## Other Resources

- [Ansible Automation Platform Self-Paced Labs
](https://red.ht/ansible-labs) - These interactive learning scenarios provide you with a pre-configured Ansible Automation Platform environment to experiment, learn, and see how the platform can help you solve real-world problems. The environment runs entirely in your browser, enabling you to learn more about our technology at your pace and time.

## YouTube Channels

- [The Ansible Playbook](https://youtube.com/ansibleautomation) - Join the Tech Marketing Engineers online here!
- [Red Hat Ansible](https://www.youtube.com/@RedHatAnsible) - Ansiblefest sessions, product announcements and more!

## Documentation

- [Ansible Getting Started Guide](https://docs.ansible.com/ansible/latest/getting_started/index.html)
- [Ansible Network Automation - Getting Started](https://docs.ansible.com/ansible/latest/network/getting_started/index.html)

## Training

- [Red Hat Training and Certification for Red Hat Ansible Automation Platform](https://red.ht/aap_training)

## Trial

- [Get a Trial Subscription for Red Hat Ansible Automation Platform](http://red.ht/try_ansible)

## Community

- [Join us on the Ansible Forum](https://forum.ansible.com/)

## Workshop Documentation

- [Workshop attendance website](docs/attendance/attendance.md)
- [How to contribute](docs/contribute.md)
- [How to use the AWS Lab Provisioner](provisioner/README.md)
- [FAQ](docs/faq.md)
- [Release Process](docs/release.md)

---
![Red Hat Ansible Automation](https://github.com/ansible/workshops/raw/devel/images/rh-ansible-automation-platform.png)
