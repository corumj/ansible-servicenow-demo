# Ansible ServiceNow Demo

## Requirements
You'll need the Ansible Networking workshop spun up 
Clone this repo to the student1 home folder on the Ansible Tower server
Update `login_info.yml` with the credentials for Tower and your ServiceNow Instance

## Setup Ansible Automation Platform for demo
Install the awx.awx collection with `ansible-galaxy collection install awx.awx`
Note: if you get an error when running the demo_setup.yml playbook complaining about allowed parameters in the credential field, you didn't install the awx.awx collection, so do that, the included tower_* modules are out of date.
Run the demo_setup playbook `ansible-galaxy demo_setup.yml` 
Check that the job templates and credentials have been setup.

## Setup ServiceNow for demo
Get yourself a ServiceNow developer instance from https://developer.servicenow.com  I typically avoid the bleeding edge type of instance and opt for one of the LTS versions

