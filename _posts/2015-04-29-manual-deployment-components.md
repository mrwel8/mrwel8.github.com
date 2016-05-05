---
published: true
layout: post
date: "2016-04-28"
comments: true
permalink: "manual-deployment-components"
title: Manual Deployment Components
---

In keeping with the tradition of (hopefully) useful, but lengthy, lists, I've started compiling all the components that can't be migrated through Change Sets. 

Salesforce actually has <a href="https://help.salesforce.com/apex/HTViewHelpDoc?id=changesets_about_components.htm" target="_blank">a list of all the components</a> that _can_ go through Change Sets, but the opposite is more helpful for planning deployments and knowing what can be done manually ahead of time. If you're using the Metadata API with Ant, then you can use <a href="https://www.salesforce.com/us/developer/docs/api_meta/Content/meta_unsupported_types.htm" target="_blank">the following list</a> of unsupported metadata types, although it seems to be outdated as of the 36.0 release.

> **Bold** indicates entire Setup menu folders <br/>

### Administer

{: .component-table}
| Feature                | Deployable?  | API Object Name    | Notes |
| ---------------------- | ------------ | ------------------ | ----- |
| Auth. Providers        | Metadata API | AuthProvider
| App Menu               | Metadata API | AppMenu
| Business Hours         | Metadata API | BusinessHoursSettings
| Company Information    | SOAP API     | Organization
| Connected Apps         | Metadata API | ConnectedApp
| CORS                   | Metadata API | CorsWhitelistOrigin
| Currency Exchange Rates| SOAP API     | DatedConversionRate
| Data.com Settings      | **No**
| Delegated Groups       | Metadata API | DelegateGroup
| **Desktop Administration** | **No**
| Divisions              | SOAP API     | Division
| Duplicate Rules        | **No**
| **Email Administration** | **No**
| File Upload and Download Security | **No**
| Fiscal Year            | Metadata API | CompanySettings
| Holidays               | Metadata API | BusinessHoursSettings
| Identity Provider      | Metadata API | SamlSsoConfig
| Language Settings      | **No**
| Login Access Policies  | **No**
| Mail Merge Templates   | SOAP API     | MailmergeTemplate
| **Mobile Administration** | Metadata API | MobileSettings
| Named Credentials      | Metadata API | NamedCredential
| Network Access         | Metadata API | SecuritySettings
| Organization-Wide Defaults| Metadata API | SharingModel
| Organization-Wide Email Addresses| SOAP API | OrgWideEmailAddress
| Password Policies      | Metadata API | SecuritySettings
| Profile Standard Object Settings & Field-Level Security| Metadata API | Profile
| Public and Resource Calendars| **No**
| Public Groups          | Metadata API | Group
| Remote Site Settings   | Metadata API | RemoteSiteSetting
| **Salesforce App for Outlook** | **No**
| Session Settings       | Metadata API | SecuritySettings
| State and Country Picklists | Metadata API | AddressSettings
| Territory Assignment Rules| Metadata API | Territory2Rule
| Translation Settings   | **No**

### Customize

{: .component-table}
| Feature                | Deployable?  | API Object Name    | Notes |
| ---------------------- | ------------ | ------------------ | ----- |
| Activity Settings      | Metadata API | ActivitiesSettings
| Approval Process order | **No**
| Button Overrides       | Metadata API | ActionOverride     | Activity Buttons Not Supported
| Campaign Influences    | **No**
| Chatter Groups         | SOAP API     | CollaborationGroup
| Chatter Settings, Chat Settings, Email Settings | **No**
| Contact Roles (Partner, Accounts & Opportunities, Opportunity Team, Cases, Case Team, Contracts) | SOAP API | PartnerRole, AccountContactRole, OpportunityContactRole, CaseContactRole, CaseTeamRole, ContractContactRole
| Contracts Settings     | Metadata API | ContractSettings
| Data Categories        | _<a href="https://developer.salesforce.com/docs/atlas.en-us.api_meta.meta/api_meta/meta_datacategorygroup.htm" target="_blank">Not Recommended</a>_ | DataCategoryGroup | Visibility Settings not supported
| Dependent picklist rules| Metadata API | Picklist
| Email-to-Case          | **No**
| Email Services         | SOAP API     | EmailServicesFunction
| Feed Item Layouts      | Metadata API | Layout
| Forecasting Settings   | Metadata API | ForecastingSettings
| Group Layouts          | Metadata API | Layout
| Home Page Standard Components| **No**
| Ideas Comment Validation Rules| Metadata API | ValidationRule
| Ideas Communities      | Metadata API | Community
| Ideas Settings         | Metadata API | IdeasSettings
| Label/Tab Renames      | Metadata API | CustomObjectTranslation
| Lead Settings          | **No**
| List Views on Standard Objects| Metadata API | ListView
| Opportunity Big Deal Alerts| **No**
| Opportunity Competitors| SOAP API     | OpportunityCompetitor
| Opportunity Product Multi-Line Layouts| Metadata API | Layout
| Opportunity Settings   | Metadata API | OpportunitySettings
| Opportunity Update Reminders| **No**
| Predefined Case Teams  | SOAP API     | CaseTeamTemplate
| Processes (Lead, Opportunity, Case, Solution)| Metadata API | BusinessProcess
| Product Schedule Setup | Metadata API | ProductSettings
| Product Settings       | Metadata API | ProductSettings
| Publisher Layouts      | Metadata API | Layout
| Quote Templates        | **No**
| Salesforce to Salesforce| **No**
| Search Layouts         | Metadata API | SearchLayouts
| Search Settings        | **No**
| Self-Service Public Solutions| **No**
| Self-Service Web-to-Case| **No**
| Social Account/Contact Settings| **No**
| Solution Categories    | SOAP API     | CategoryNode
| Solution Settings      | **No**
| Standard auto-number & system fields| **No**
| Standard Field History | Metadata API | CustomField
| Standard Picklists     | Metadata API | Picklist           | With exceptions<sup>†</sup>
| Support Settings       | Metadata API | CaseSettings
| Tag Settings           | **No**
| Teams (Account, Opportunity, Case)| SOAP API| AccountTeamMember, OpportunityTeamMember, CaseTeamMember
| User Interface Settings| Metadata API | ActivitiesSettings & NameSettings | Partially supported
| Web-to-Lead            | **No**

> † Lead.CampaignMemberStatus, Opportunity.ForecastCategoryName, and Order.Status are not supported. <br/> For CampaignMember.LeadSource & Contact.LeadSource & Lead.LeadSource & Opportunity.LeadSource ⇒ Account.AccountSource <br/> For Lead.Industry ⇒ Account.Industry <br/> For Lead.Rating ⇒ Account.Rating <br/> For Contact.Salutation & Lead.Salutation ⇒ CampaignMember.Salutation

### Other Items to Verify
* Visual Workflow & Process Builder flows need to be activated
* Custom Buttons that use the <a href="http://raydehler.com/cloud/clod/salesforce-url-hacking-to-prepopulate-fields-on-a-standard-page-layout.html" target="_blank">well-document URL hacking</a> with field IDs or Object prefixes
* Formulas that reference Documents, Static Resources, Record Types, or IDs
* My Settings (Personal Groups, Display & Layout, Email, Chatter, Calendar & Reminders)
* Deployment Settings
