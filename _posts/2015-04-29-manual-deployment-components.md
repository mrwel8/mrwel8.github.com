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

> If you're using the Metadata API with Ant, then you can use <a href="https://www.salesforce.com/us/developer/docs/api_meta/Content/meta_unsupported_types.htm" target="_blank">the following list</a> of unsupported metadata types.

### Administer Section
* Company Profile > Business Hours
* Security Controls > Sharing Settings > Organization-Wide Defaults
* Security Controls > Password Policies
* Security Controls > Session Settings
* **All** Mobile Administration
* Desktop Administration > Outlook Configurations

### Build Section
* Customize > Tab Names and Labels
* Customize > Home > Home Page Components > Standard Components
* Customize > Activities > Activity Settings
* Customize > **All Standard Field Values** (including Picklist Values & Auto-Number Formats)
* Customize > **All Partner & Contact Roles** (including Account & Case Teams)
* Customize > Cases > Email-2-Case
* Create > Apps > Connected Apps

### Other Items
* Chatter Groups
