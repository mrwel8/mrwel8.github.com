---
published: true
layout: post
date: "2016-04-28"
comments: true
permalink: "manual-deployment-components"
title: Manual Deployment Components
---

In keeping with the tradition of (hopefully) useful, but lengthy, lists, I've started compiling all the components that can't be migrated through Change Sets. 

Salesforce actually has <a href="https://help.salesforce.com/apex/HTViewHelpDoc?id=changesets_about_components.htm" target="_blank">a list of all the components</a> that _can_ go through Change Sets, but the opposite is more helpful for planning deployments and knowing what can be done manually ahead of time. If you're using the Metadata API with Ant, then you can use <a href="https://www.salesforce.com/us/developer/docs/api_meta/Content/meta_unsupported_types.htm" target="_blank">the following list</a> of unsupported metadata types, all of which are contained below as well.

> **Bold** indicates entire Setup menu folders <br/>
> Point links to <input id="prod-toggle" type="checkbox" checked data-toggle="toggle" data-on="Prod" data-off="Sandbox" data-onstyle="success" data-offstyle="primary">

### Administration
{: .component-table}
| Feature                | Deployable?  | API Object Name    | Notes |
| ---------------------- | ------------ | ------------------ | ----- |
| Business Hours         | Metadata API | BusinessHoursSettings

### Build
{: .component-table}
| Feature                | Deployable?  | API Object Name    | Notes |
| ---------------------- | ------------ | ------------------ | ----- |
| Activity Settings      | Metadata API | ActivitiesSettings 
| Approval Process order | **No**
| Button Overrides       | Metadata API | ActionOverride     | Activity Buttons Not Supported
| Campaign Influences    | **No**
| Chatter Groups         | SOAP API     | CollaborationGroup
| Chatter Settings, Chat Settings, Email Settings | **No**
| Connected Apps         | Metadata API | ConnectedApp
| Contact Roles (Partner, Account, Oppty, Oppty Team, Cases, Case Team, Contracts) | SOAP API | AccountContactRole, CaseContactRole, ContractContactRole, OpportunityContactRole, Partner
| Contracts Settings     | Metadata API | ContractSettings
| Currency Exchange Rates| SOAP API     | DatedConversionRate
| Data Categories        | _<a href="https://developer.salesforce.com/docs/atlas.en-us.api_meta.meta/api_meta/meta_datacategorygroup.htm" target="_blank"> Not Recommended</a>_ | DataCategoryGroup | Visibility Settings not supported
| Delegated Administration| **No**
| Dependent picklist rules| Metadata API | Picklist
| **Desktop Administration** | **No**
| Divisions              | SOAP API     | Division        
| **Email Administration**  | **No**
| Email Services         | SOAP API     | EmailServicesFunction
| Email-to-Case          | **No**
| Feed Item Layouts      | Metadata API | Layout
| Fiscal Year            | Metadata API | CompanySettings
| Forecasting Settings   | Metadata API | ForecastingSettings
| Group Layouts          | Metadata API | Layout
| Holidays               | Metadata API | BusinessHoursSettings
| Home Page Standard Components| **No**
| Ideas Comment Validation Rules| Metadata API | ValidationRule
| Ideas Communities      | Metadata API | Community
| Ideas Settings         | Metadata API | IdeasSettings
| Label/Tab Renames      | Metadata API | CustomObjectTranslation
| Lead Settings          | **No**
| List Views on Standard Objects| Metadata API | ListView
| Mail Merge Templates   | SOAP API     | MailmergeTemplate
| **Mobile Administration** | **No**
| Opportunity Big Deal Alerts| **No**
| Opportunity Competitors| SOAP API     | OpportunityCompetitor
| Opportunity Product Multi-Line Layouts| Metadata API | Layout
| Opportunity Settings   | Metadata API | OpportunitySettings
| Opportunity Update Reminders| **No**
| Organization-Wide Defaults| Metadata API | SharingModel
| Organization-Wide Email Addresses| SOAP API | OrgWideEmailAddress
| Password Policies      | Metadata API | SecuritySettings
| Predefined Case Teams  | SOAP API     | CaseTeamTemplate
| Processes (Lead, Oppty, Cases, Solution)| Metadata API | BusinessProcess
| Product Schedule Setup | Metadata API | ProductSettings
| Product Settings       | Metadata API | ProductSettings
| Profile Standard Object Settings & Field-Level Security| Metadata API | Profile
| Public and Resource Calendars| **No**
| Public Groups          | Metadata API | Group
| Publisher Layouts      | Metadata API | Layout
| Queues                 | Metadata API | Queue
| Quote Templates        | **No**
| Role Hierarchies       | Metadata API | Role
| Salesforce to Salesforce| **No**
| Search Layouts         | Metadata API | SearchLayouts
| Search Settings        | **No**
| Self-Service Public Solutions| **No**
| Self-Service Web-to-Case| **No**
| Session Settings       | Metadata API | SecuritySettings
| Sharing Rules          | Metadata API | SharingRules
| _Site.com Content_     | _Has own process_
| Social Account/Contact Settings| **No**
| Solution Categories    | SOAP API     | CategoryNode
| Solution Settings      | **No**
| Standard auto-number & system fields| **No**
| Standard Field History | Metadata API | CustomField
| Standard Picklists     | Metadata API | Picklist           | With exceptions<sup>†</sup>
| Support Settings       | Metadata API | CaseSettings
| Tag Settings           | **No**
| Teams (Account, Oppty, Case)| SOAP API| AccountTeamMember, OpportunityTeamMember, CaseTeamMember
| Territory Assignment Rules| Metadata API | Territory2Rule
| User Interface Settings| Metadata API | ActivitiesSettings & NameSettings | Partially supported
| Web-to-Lead            | **No**

> † Lead.CampaignMemberStatus, Opportunity.ForecastCategoryName, and Order.Status are not supported. <br/> For CampaignMember.LeadSource & Contact.LeadSource & Lead.LeadSource & Opportunity.LeadSource ⇒ Account.AccountSource <br/> For Lead.Industry ⇒ Account.Industry <br/> For Lead.Rating ⇒ Account.Rating <br/> For Contact.Salutation & Lead.Salutation ⇒ CampaignMember.Salutation

### Other Items to Verify
* Visual Workflow & Process Builder flows need to be activated
* Custom Buttons that use the <a href="http://raydehler.com/cloud/clod/salesforce-url-hacking-to-prepopulate-fields-on-a-standard-page-layout.html" target="_blank">well-document URL hacking</a> with field IDs or Object prefixes
* Formulas that reference Documents, Static Resources, Record Types, or IDs
* <a class="dyn-link" href="https://login.salesforce.com/ui/setup/Setup?setupid=PersonalSetup" target="_blank">My Settings</a>
* <a class="dyn-link" href="https://login.salesforce.com/changemgmt/deploymentSettings.apexp" target="_blank">Deployment Settings</a>