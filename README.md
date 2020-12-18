# Ansible ServiceNow Demo

Simple to setup version of this demo: https://github.com/ansible/workshops/tree/devel/demos/servicenow/2-closed_loop_incident_mgmt

This demo showcases Tower's ability to reach into ServiceNow to create tickets, as well as ServiceNow being able to reach into Tower's API to trigger an automation template.

## Requirements
You'll need the Ansible Networking workshop spun up
You will need a ServiceNow developer Instance 

Install the awx.awx collection from the terminal with `ansible-galaxy collection install awx.awx`

Using the included VS Code server, and the terminal, open the studentX home folder in the terminal and clone this repository.

Create a copy of the `login_info_template.yml` named `login_info.yml` and fill out the required information for Tower and your ServiceNow Instance. 

## Setup Ansible Automation Platform for demo
Run the demo_setup playbook `ansible-playbook demo_setup.yml` 

Note: if we get an error when running the demo_setup.yml playbook complaining about allowed parameters in the credential field, we didn't install the awx.awx collection, so do that.

Check that the job templates and credentials have been setup in Ansible Tower.
In ServiceNow, Search for REST Message and verify you have an Ansible Tower Demo REST Message