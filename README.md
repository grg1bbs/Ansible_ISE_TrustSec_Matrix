# Ansible_ISE_TrustSec_Matrix
Ansible playbook for creating Security Group Tags (SGTs), Security Group Access Control Lists (SGACLs), and TrustSec Egress Policy Matrix Cell configurations

This playbook was validated using:
 - ISE 3.2 patch 4
 - Ansible 2.15.5
 - CiscoISESDK 2.1.2
 - ISE Ansible collection 2.6.1

## ISE Pre-requisites
The following ISE configurations are required prior to running this playbook:

 1. An administrator account with the 'ERS Admin' role

## TrustSec Policies and Policy Elements created
The following Policy Elements and Policy Sets are created by this playbook:

### Policy Elements

 - New Security Group Tag (SGT) named "Shared_Services"
 - New Security Group ACLs (SGACLs)
   - DENY_IP_ANY (deny ip any any)
   - PERMIT_IP_ANY (permit ip any any)

### Egress Policy Cells

Employees to Developers
 - Source SGT 'Employees' (default SGT) & Destination SGT 'Developers (default SGT)
 - SGACL 'DENY_IP_ANY' applied
Employees to Shared_Services
 - Source SGT 'Employees' (default SGT) & Destination SGT 'Shared_Services'
 - SGACL 'PERMIT_IP_ANY' applied

## Ansible Pre-requisites
Running this playbook requires Python and Ansible software installed.
If you have any problems installing Python or Ansible, see [Installing Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

Using Ansible to interact with the Cisco ISE API also requires the Cisco ISE SDK and Ansible Collection.
See [Ansible Modules for Cisco ISE](https://github.com/CiscoISE/ansible-ise) for more information.

## Quick Start
1. Clone this repository:  

    ```bash
    git clone https://github.com/grg1bbs/Ansible_ISE_TrustSec_Matrix
    ```
 
2. Edit the following files to suit your environment:
 - credentials.yaml
 - hosts

4. Run the Ansible playbook

    ```bash
    ansible-playbook -i hosts cts-matrix.yaml
    ```
