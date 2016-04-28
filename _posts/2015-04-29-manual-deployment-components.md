---
published: true
layout: post
date: "2016-04-28"
comments: true
permalink: "manual-deployment-components"
title: Manual Deployment Components
---

In keeping with the tradition of (hopefully) useful, but lengthy, lists, I've started compiling all the components that can't be migrated through Change Sets. 

Salesforce actually has <a href="https://www.salesforce.com/us/developer/docs/api_meta/Content/meta_unsupported_types.htm" target="_blank">a list of all the components</a> that _can_ go through Change Sets, but the opposite is more helpful for planning deployments and knowing what can be done manually ahead of time. 

> If you're using the Metadata API with Ant, then you can use <a href="https://www.salesforce.com/us/developer/docs/api_meta/Content/meta_unsupported_types.htm" target="_blank">the following list</a> of unsupported metadata types, nearly all of which are contained below as well.

| Feature                | Metadata API? | API Object Name    | Notes |
| ---------------------- | ------------- | ------------------ | ----- |
| Activity Settings      | Yes           | ActivitiesSettings |       |
| Approval Process order | No            |                    |       |
| Business Hours|TRUE|BusinessHoursSettings|
| Button Overrides|TRUE|ActionOverride|Activity Buttons Not Supported
| Campaign Influences|FALSE||
| Chatter Groups|TRUE|CollaborationGroup|SOAP API
| Chatter Settings, Chat Settings, Email Settings|FALSE||
| Connected Apps|TRUE|ConnectedApp|
| Console Layouts|FALSE||
| Contact Roles (Partner, Account, Oppty, Oppty Team, Cases, Case Team, Contracts)|TRUE|AccountContactRole, CaseContactRole, | | | ContractContactRole, OpportunityContactRole, Partner|SOAP API
| Contracts Settings|TRUE|ContractSettings|
| Currency Exchange Rates|TRUE|DatedConversionRate|SOAP API
| Data Categories|TRUE|DataCategoryGroup|Visibility Settings not supported
| Delegated Administration|FALSE||
| Dependent picklist rules|TRUE|Picklist|
| Desktop Administration|FALSE||
| Divisions|TRUE|Division|SOAP API
| Email Administration|FALSE||
| Email Services|TRUE|EmailServicesFunction|SOAP API
| Email-to-Case|FALSE||
| Feed Item Layouts|TRUE|Layout|
| Fiscal Year|TRUE|CompanySettings|
| Forecasting Settings|TRUE|ForecastingSettings|
| Group Layouts|TRUE|Layout|
| Holidays|TRUE|BusinessHoursSettings|
| Home Page Standard Components|FALSE||
| Ideas Comment Validation Rules |TRUE|ValidationRule|
| Ideas Communities|TRUE|Community|
| Ideas Settings|TRUE|IdeasSettings|
| Label/Tab Renames|TRUE|CustomObjectTranslation|
| Lead Settings|FALSE||
| List Views on Standard Objects|TRUE|ListView|
| Mail Merge Templates|TRUE|MailmergeTemplate|SOAP API
| Mobile Administration|FALSE||
| Opportunity Big Deal Alerts|FALSE||
| Opportunity Competitors|TRUE|OpportunityCompetitor|SOAP API
| Opportunity Product Multi-Line Layouts|TRUE|Layout|
| Opportunity Settings |TRUE|OpportunitySettings|
| Opportunity Update Reminders|FALSE||
| Organization-Wide Defaults |TRUE|SharingModel|
| Organization-Wide Email Addresses|TRUE|OrgWideEmailAddress|SOAP API
| Password Policies|TRUE|SecuritySettings|
| Predefined Case Teams|TRUE|CaseTeamTemplate|SOAP API
| Processes (Lead, Oppty, Cases, Solution)|TRUE|BusinessProcess|
| Product Schedule Setup|TRUE|ProductSettings|
| Product Settings|TRUE|ProductSettings|
| Profile Standard Object Settings & Field-Level Security|TRUE|Profile|
| Public and Resource Calendars|FALSE||
| Public Groups|TRUE|Group|
| Publisher Layouts|TRUE|Layout|
| Queues|TRUE|Queue|
| Quote Templates|FALSE||
| Role Hierarchies|TRUE|Role|
| Salesforce to Salesforce|FALSE||
| Search Layouts|TRUE|SearchLayouts|
| Search Settings|FALSE||
| Self-Service Public Solutions|FALSE||
| Self-Service Web-to-Case|FALSE||
| Session Settings|TRUE|SecuritySettings|
| Sharing Rules|TRUE|SharingRules|
| Site.com Content|Has own process||
| Social Account/Contact Settings|FALSE||
| Solution Categories|TRUE|CategoryNode|SOAP API
| Solution Settings|FALSE||
| Standard auto-number & system fields|FALSE||
| Standard Field History|TRUE|CustomField|
| Standard Picklists|TRUE|Picklist|Except Lead.CampaignMemberStatus, Opportunity.ForecastCategoryName, and Order.Status <br/> For Source (Account, Lead, Contact, Oppty, Camp Mem), use Account.AccountSource <br/> For Industry (Account, Lead), use Account.Industry <br/> For Rating (Account, Lead), use Account.Rating <br/> For Salutation (Lead, Contact, Camp Mem), use CampaignMember.Salutation|
| Support Settings|TRUE|CaseSettings|
| Tag Settings|FALSE||
| Teams (Account, Oppty, Case)|TRUE|AccountTeamMember, OpportunityTeamMember, CaseTeamMember|SOAP API
| Territory Assignment Rules|TRUE|Territory2Rule|
| User Interface Settings|TRUE|ActivitiesSettings, NameSettings|Not all supported
| Web-to-Lead|FALSE||


### Administer Section


### Build Section


### Other Items to Verify
* Default List Views on Standard Objects
* Chatter Groups
* Approval Process Order
* Visual Workflow & Process Builder flows (need to be activated)
* Custom Buttons that use the <a href="http://raydehler.com/cloud/clod/salesforce-url-hacking-to-prepopulate-fields-on-a-standard-page-layout.html" target="_blank">well-document URL hacking</a> with field IDs or Object prefixes
* Formulas that reference Documents, Static Resources, Record Types, or IDs
