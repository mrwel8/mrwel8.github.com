---
published: true
layout: post
date: "2015-10-26"
comments: true
permalink: "email-limits"
title: Deciphering Email Size Limits
---





Having gone back and forth with Salesforce Technical Support a few times on the issue of email & attachment sizes and experienced it first-hand, I wanted to provide some clarity on the 5, 10, and 25 MB numbers floating around the help docs. 

### Inbound Email
- Approx. **18 MB** for all attachments (25 MB for the entire email, including headers and encoding)
- **No** individual attachment size limit
> Includes Email-to-Case, standard and on-demand, and Apex email services

### Outbound Email
- **10 MB** for all attachments
- **No** individual attachment size limit (5 MB when attaching from a Document)
