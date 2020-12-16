# Ansible ServiceNow Demo

## Requirements
You'll need the Ansible Networking workshop spun up

Using the included VS Code server, and the terminal, open the studentX home folder in the terminal and clone this repository.

Install the awx.awx collection from the terminal with `ansible-galaxy collection install awx.awx`

Note: if we get an error when running the demo_setup.yml playbook complaining about allowed parameters in the credential field, we didn't install the awx.awx collection, so do that.

Update `login_info.yml` with the credentials for Tower and your ServiceNow Instance

## Setup Ansible Automation Platform for demo
Run the demo_setup playbook `ansible-galaxy demo_setup.yml` 

Check that the job templates and credentials have been setup in Ansible Tower.

Follow the instructions here for setting up the ServiceNow REST Message and Business Rule: [SNOW Demo](https://github.com/ansible/workshops/tree/devel/demos/servicenow/2-closed_loop_incident_mgmt)

## Setup ServiceNow for demo
Get yourself a ServiceNow developer instance from https://developer.servicenow.com  I typically avoid the bleeding edge type of instance and opt for one of the LTS versions

When you have the instance, you'll need to use the navigation filter and enter `sys_properties.list`
When that opens, click New and set the following:

| Field | value |
| ----- | ----- |
| Name  | com.glide.communications.httpclient.verify_revoked_certificate |
| Type  | True/False |
| value | false |

