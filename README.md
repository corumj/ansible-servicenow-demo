# Ansible ServiceNow Demo

This is a simple to setup version of this demo: https://github.com/ansible/workshops/tree/devel/demos/servicenow/2-closed_loop_incident_mgmt

This demo showcases Tower's ability to update ServiceNow tickets when it finds a compliance issue.  It also leverages a ServiceNow Business rule to react to the creation of a ticket and perform an automation by triggering an Ansible job template to run via Tower's REST API.

## Requirements
* Ansible-demo Tower Instance setup following instructions here: https://github.com/corumj/ansible-demo
* ServiceNow Developer Instance 
  * Tested with New York and Paris versions

## Setup Ansible Automation Platform for demo

1. In the Ansible-demo Tower instance, there will be a template called "Select a demo to stage".  Run that and from the drop down select "ServiceNow".
2. Once that completes, you'll have a new template called SNOW- Initialize Demo.  This is the point where the demo will provision a Windows Server as well as setup the REST Message and Business Rule in ServiceNow.  Run this template, fill out the survey with the SNOW connection info, and wait.

## Running the demo
You'll have two new Job Templates:
1. SNOW-Demo-Compliance-Check
2. SNOW-Demo-Compliance-Fix

These are actually pointed to the same playbook, `check_compliance.yml` but use tags to change the behavior (check and fix).
I start with letting people know we have a simple compliance check that's checking some registry settings on a Windows server but we need to know and document when those systems are out of compliance.  Good chance to talk about scheduling jobs as well.

Run the SNOW-Demo-Compliance-Check job template and talk through the log output.  Emphasize "check mode" vs "run mode".  Here it's checking the windows server for compliance, oh something was yellow and should be changed to meet compliance rules, so the template makes a ticket in SNOW.  Could expand the ticket with more details as well, this is just a basic example.  

Once that job completes, I like to pop over to the Job List and show that, while we didn't trigger it, the SNOW-Demo-Compliance-Fix template has been triggered and is running to fix the compliance issue.  Automatic Automation!  

Pop into ServiceNow and show the ticket.  Walk through the updates from bottom to top.  
Tower created the ticket and noted which server was out of compliance.
Tower set the defaults we want for severity, priority, etc..  
Business Rule kicks in and updates the ticket with "Contacting Ansible Tower to fix bespoke incident".  
The remaining updates in that ticket come from the SNOW-Demo-Compliance-Fix, confirming the fix was implemented, resolving and closing the ticket.

Sometimes I show folks the Business Rule and REST Message if they're interested in how the soup was made.  