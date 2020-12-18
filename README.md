# Ansible ServiceNow Demo

This is a simple to setup version of this demo: https://github.com/ansible/workshops/tree/devel/demos/servicenow/2-closed_loop_incident_mgmt

This demo showcases Tower's ability to update ServiceNow tickets when it finds a compliance issue.  It also leverages a ServiceNow Business rule to react to the creation of a ticket and perform an automation by triggering an Ansible job template to run via Tower's REST API.

## Requirements
* Ansible Networking workshop spun up
* ServiceNow Developer Instance 

## Setup Ansible Automation Platform for demo
1. Install the awx.awx collection from the terminal with `ansible-galaxy collection install awx.awx`
2. Using the included VS Code server, and the terminal, open the studentX home folder in the terminal and clone this repository.
3. Create a copy of the `login_info_template.yml` named `login_info.yml` and fill out the required information for Tower and your ServiceNow Instance. 
4. Run the demo_setup playbook `ansible-playbook demo_setup.yml` 

Note: if we get an error when running the demo_setup.yml playbook complaining about allowed parameters in the credential field, we didn't install the awx.awx collection, so do that.

Check that the job templates and credentials have been setup in Ansible Tower.
In ServiceNow, Search for REST Message and verify you have an Ansible Tower Demo REST Message