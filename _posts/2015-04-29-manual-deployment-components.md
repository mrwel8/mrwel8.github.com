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

> If you're using the Metadata API with Ant, then you can use <a href="https://www.salesforce.com/us/developer/docs/api_meta/Content/meta_unsupported_types.htm" target="_blank">the following list</a> of unsupported metadata types, all of which are contained below as well.

| Feature                | Metadata API? | SOAP API? | API Object Name    | Notes |
| ---------------------- | ------------- | --------- | ------------------ | ----- |
| Activity Settings      | Yes           |           | ActivitiesSettings 
| Approval Process order | No
| Business Hours         | Yes           |           | BusinessHoursSettings
| Button Overrides       | Yes           |           | ActionOverride     | Activity Buttons Not Supported
| Campaign Influences    | No
| Chatter Groups         | No            | Yes       | CollaborationGroup
| Chatter Settings, Chat Settings, Email Settings | No
| Connected Apps         | Yes           |           | ConnectedApp
| Console Layouts        | No
| Contact Roles (Partner, Account, Oppty, Oppty Team, Cases, Case Team, Contracts) | No | Yes | AccountContactRole, CaseContactRole, ContractContactRole, OpportunityContactRole, Partner
| Contracts Settings     | Yes           |           | ContractSettings
| Currency Exchange Rates| No            | Yes       | DatedConversionRate
| Data Categories        | Yes           |           | DataCategoryGroup  | Visibility Settings not supported
| Delegated Administration| No
| Dependent picklist rules| Yes          |           | Picklist
| **Desktop Administration** | No
| Divisions              | No            | Yes       | Division        
| **Email Administration**  | No
| Email Services         | No            | Yes       | EmailServicesFunction
| Email-to-Case          | No
| Feed Item Layouts      | Yes           |           | Layout
| Fiscal Year            | Yes           |           | CompanySettings
| Forecasting Settings   | Yes           |           | ForecastingSettings
| Group Layouts          | Yes           |           | Layout
| Holidays               | Yes           |           | BusinessHoursSettings
| Home Page Standard Components| No
| Ideas Comment Validation Rules| Yes    |           | ValidationRule
| Ideas Communities      | Yes           |           | Community
| Ideas Settings         | Yes           |           | IdeasSettings
| Label/Tab Renames      | Yes           |           | CustomObjectTranslation
| Lead Settings          | No
| List Views on Standard Objects| Yes    |           | ListView
| Mail Merge Templates   | No            | Yes       | MailmergeTemplate
| **Mobile Administration** | No
| Opportunity Big Deal Alerts| No
| Opportunity Competitors| No            | Yes       | OpportunityCompetitor
| Opportunity Product Multi-Line Layouts| Yes |      | Layout
| Opportunity Settings   | Yes           |           | OpportunitySettings
| Opportunity Update Reminders| No
| Organization-Wide Defaults| Yes        |           | SharingModel
| Organization-Wide Email Addresses| No  | Yes       | OrgWideEmailAddress
| Password Policies      | Yes           |           | SecuritySettings
| Predefined Case Teams  | No            | Yes       | CaseTeamTemplate
| Processes (Lead, Oppty, Cases, Solution)| Yes | BusinessProcess
| Product Schedule Setup | Yes           |           | ProductSettings
| Product Settings       | Yes           |           | ProductSettings
| Profile Standard Object Settings & Field-Level Security| Yes | | Profile
| Public and Resource Calendars| No
| Public Groups          | Yes           |           | Group
| Publisher Layouts      | Yes           |           | Layout
| Queues                 | Yes           |           | Queue
| Quote Templates        | No
| Role Hierarchies       | Yes           |           | Role
| Salesforce to Salesforce| No
| Search Layouts         | Yes           |           | SearchLayouts
| Search Settings        | No
| Self-Service Public Solutions| No
| Self-Service Web-to-Case| No
| Session Settings       | Yes           |           | SecuritySettings
| Sharing Rules          | Yes           |           | SharingRules
| _Site.com Content_     | _Has own process_
| Social Account/Contact Settings| No
| Solution Categories    | No            | Yes       | CategoryNode
| Solution Settings      | No
| Standard auto-number & system fields| No
| Standard Field History | Yes           |           | CustomField
| Standard Picklists     | Yes           |           | Picklist           | Except Lead.CampaignMemberStatus, Opportunity.ForecastCategoryName, and Order.Status <br/> For Source (Account, Lead, Contact, Oppty, Camp Mem), use Account.AccountSource <br/> For Industry (Account, Lead), use Account.Industry <br/> For Rating (Account, Lead), use Account.Rating <br/> For Salutation (Lead, Contact, Camp Mem), use CampaignMember.Salutation
| Support Settings       | Yes           |           | CaseSettings
| Tag Settings           | No
| Teams (Account, Oppty, Case)| No       | Yes       | AccountTeamMember, OpportunityTeamMember, CaseTeamMember
| Territory Assignment Rules| Yes        |           | Territory2Rule
| User Interface Settings| Yes           |           | ActivitiesSettings, NameSettings | Not all supported
| Web-to-Lead            | No


### Administer Section


### Build Section


### Other Items to Verify
* Default List Views on Standard Objects
* Chatter Groups
* Approval Process Order
* Visual Workflow & Process Builder flows (need to be activated)
* Custom Buttons that use the <a href="http://raydehler.com/cloud/clod/salesforce-url-hacking-to-prepopulate-fields-on-a-standard-page-layout.html" target="_blank">well-document URL hacking</a> with field IDs or Object prefixes
* Formulas that reference Documents, Static Resources, Record Types, or IDs
