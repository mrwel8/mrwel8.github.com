---
published: true
layout: post
date: "2015-04-29"
comments: true
permalink: "manual-deployment-components"
title: Manual Deployment Components
---

In keeping with the tradition of (hopefully) useful, but lengthy, lists, I've started compiling all the components that can't be migrated through Change Sets. 

Salesforce actually has <a href="https://www.salesforce.com/us/developer/docs/api_meta/Content/meta_unsupported_types.htm" target="_blank">a list of all the components</a> that _can_ go through Change Sets, but the opposite is more helpful for planning deployments and knowing what can be done manually ahead of time. 

> If you're using the Metadata API with Ant, then you can use <a href="https://www.salesforce.com/us/developer/docs/api_meta/Content/meta_unsupported_types.htm" target="_blank">the following list</a> of unsupported metadata types, nearly all of which are contained below as well.

### Administer Section
* Manage Users > Profiles > Assigned Apps
* Manage Users > Profiles > Standard Object Settings & Field-Level Security
* Company Profile > Fiscal Year, Business Hours, Holidays
* Security Controls > Sharing Settings > Organization-Wide Defaults
* Security Controls > Password Policies, Session Settings
* Communication Templates > Mail Merge Templates
* **All** Mobile Administration
* **All** Desktop Administration (including Outlook Configurations)
* Email Administration > Organization-Wide Email Addresses

### Build Section
* Customize > Tab Names and Labels
* Customize > Home > Home Page Components > Standard Components
* Customize > **All Standard Field Values** (including Picklist Values & Auto-Number Formats)
* Customize > **All Button Overrides**
* Customize > **All Partner & Contact Roles** (including Account & Case Teams)
* Customize > Activities > Activity Settings
* Customize > Leads > Settings
* Customize > Leads > Web-2-Lead
* Customize > Opportunities > Big Deal Alert, Update Reminders
* Customize > Cases > Support Settings
* Customize > Cases > Email-2-Case
* Customize > Solutions > Solution Categories
* Customize > Solutions > Solution Settings
* Customize > Products > Schedule Setup
* Customize > Tags > Tag Settings
* Customize > Search > Search Settings
* Customize > Chatter > Settings, Chat Settings, Email Settings
* Customize > Social Apps Integration > Social Accounts and Contacts > Settings
* Customize > User Interface
* Create > Apps > Connected Apps

### Other Items to Verify
* Default List Views on Standard Objects
* Chatter Groups
* Approval Process Order
* Visual & Process Builder Flows (need to be activated)
* Custom Buttons that use the <a href="http://raydehler.com/cloud/clod/salesforce-url-hacking-to-prepopulate-fields-on-a-standard-page-layout.html" target="_blank">well-document URL hacking</a> with field IDs or Object prefixes
* Formulas that reference Documents, Static Resources, Record Types, or IDs