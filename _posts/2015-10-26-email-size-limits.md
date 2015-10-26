---
published: true
layout: post
date: "2015-10-26"
comments: true
permalink: "email-size-limits"
title: Deciphering Email Size Limits
---







Having gone back and forth with Salesforce Technical Support and experienced first-hand the question of email & attachment sizes, I wanted to provide some clarity on the 5, 10, and 25 MB numbers floating around the help docs. 

### Inbound Email
> Includes on-demand Email-to-Case and Apex email services

- Approx. **18 MB** for all attachments
  * 25 MB for the entire email, including headers and encoding
- **No** individual attachment size limit

> "Standard" Email-to-Case does not have Salesforce limits since emails remain on the email server

### Outbound Email
> Includes email templates and Apex Messaging methods

- **10 MB** for all attachments
- **No** individual attachment size limit
  * 5 MB when attaching from a Document
