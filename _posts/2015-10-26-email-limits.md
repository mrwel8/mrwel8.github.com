---
published: true
layout: post
date: "2015-10-26"
comments: true
permalink: "email-limits"
title: Deciphering Email Size Limits
---





Having gone back and forth with Salesforce Technical Support a few times on the issue of email & attachment sizes, I wanted to provide some clarity on the 5, 10, and 25 MB numbers floating around the help docs. 

### Email Services
- Approx. **18 MB** for all attachments (25 MB for the entire email, including headers and encoding)
- **No** individual attachment size limit
> Includes Email-to-Case, standard and on-demand, or Apex Services

### Outbound Email
- **25 MB** for all attachments
- **5 MB** per attachment (Document file limit)

