---
published: true
layout: post
date: "2015-05-14"
comments: true
permalink: "thoughts-on-wave"
title: Thoughts on Wave
---


I had the chance back in November to go to New York for training on Salesforce's newest feature – Salesforce Analytics Cloud – and ever since, people have asked me:

_"What do you think about Wave?"_

In a nutshell, it's **awesome** :grin:

> The training was a 3-day "Brown Belt" course, which is the closest equivalent Salesforce currently has to an implementation expert certification... There's some more sessions going on right now, so ask your Account Executive or Partner Manager if you're interested!

### It's come a very long way since last November
Back in November, there were a lot of moments where you had to dig into code in order to import datasets, transform the data, or fully configure a dashboard. While you still have the option to use code to do all that, I'm happy to report that that's no longer the case!

As of the Summer '15 release, you can now:

* <a href="https://help.salesforce.com/apex/HTViewHelpDoc?id=bi_dataset_builder.htm&language=en_US" target="_blank">Build datasets from Salesforce data through a UI</a>
* <a href="http://releasenotes.docs.salesforce.com/en-us/summer15/release-notes/rn_bi_csv_preview.htm" target="_blank">Edit dataset metadata without editing JSON code</a>
* <a href="http://releasenotes.docs.salesforce.com/en-us/summer15/release-notes/rn_bi_wave_public_api.htm#rn_bi_wave_public_api" target="_blank">Access datasets through a REST API</a>
* <a href="http://releasenotes.docs.salesforce.com/en-us/summer15/release-notes/rn_bi_embedded_dashboard.htm#rn_bi_embedded_dashboard" target="_blank">Add AC dashboards to Salesforce detail pages</a>

### It's now very much Salesforce-centric
When Analytics Cloud was first being marketed, Salesforce emphasized that any data, structured or unstructured, could be imported. Since then, they've refocused their pitch on using Salesforce data as the key component, with other data sources as "decoration", or <a href="https://help.salesforce.com/apex/HTViewHelpDoc?id=bi_integrate_augment_transformation.htm&language=en_US" target="_blank">augmenting</a> the Salesforce pieces. 

<img src="https://help.salesforce.com/resource/HTHelpDocImages_194_20_en_US_8/bi_dashboard_example.png" alt="Analytics Cloud Dashboard"/>

### The technology has been around for a while
Although the Salesforce page on this topic looks pretty impressive, the technology that powers Wave is actually not as novel as you might think. Key-value store databases have been around since the 70s, SAQL is essentially a customization of Apache Pig, and EdgeSpring (the company bought by Salesforce in 2013 for an undisclosed sum) had been developing the Edgemart and visualization features since at least 2010. The difference of course has been combining them all together into one sleek-looking package.

### Salesforce has a lot of ideas in the roadmap
One giant advantage of being a <a href="https://appexchange.salesforce.com/listingDetail?listingId=a0N30000009xUI8EAM" target="_blank">Gold Partner</a> is that product managers sometimes give you glimpses into what is in the pipeline. Without going against any NDA or #safeharbor, all I can say is that Salesforce is putting a ton of effort into Analytics Cloud, so much so that their release timetable is actually doubled compared to the standard Winter / Spring / Summer schedule. The product team seems well aware of AC's shortcomings, and is already thinking through some really neat features for the near- and long-term future.

### It's more popular than you might think
Trust me when I say that some **very** big EBUs (Enterprise Business Units) are already using Analytics Cloud. Actually, you don't need to trust me since Salesforce is now <a href="http://www.salesforce.com/analytics-cloud/resources/" target="_blank">publicizing those</a>: Coca Cola, GE Capital, Blue Cross Blue Shield, EMC, Akamai,... Sure, they probably have some other analytics platforms running as well, but who knows how long that will last!

### It's expensive, but likely worth it
Sure, the numbers look pretty big on the <a href="http://www.salesforce.com/analytics-cloud/pricing/" target="_blank">Salesforce website</a>, but think about what you're getting – A cloud-based analytics platform that is instantly mobile-enabled and connected to your Salesforce data, without any extra infrastructure costs. When you look at competitors, they are either much more technical to implement (Informatica, Tableau), or they're built for only IT to use (SAP BO, Oracle BI).

> Besides, there are some discounts going around **right now** that I can help you <script type="text/javascript" language="javascript">
<!--
// Email obfuscator script 2.1 by Tim Williams, University of Arizona
// Random encryption key feature by Andrew Moulden, Site Engineering Ltd
// This code is freeware provided these four comment lines remain intact
// A wizard to generate this code is at http://www.jottings.com/obfuscator/
{ coded = "wU8dDF9@c8f892.592"
  key = "nWR6kIrsAPHVDSgji7FZGLMaKcJhb1mq4wdylT0Qufo5CpYO2zN3Et8BeXUx9v"
  shift=coded.length
  link=""
  for (i=0; i<coded.length; i++) {
    if (key.indexOf(coded.charAt(i))==-1) {
      ltr = coded.charAt(i)
      link += (ltr)
    }
    else {     
      ltr = (key.indexOf(coded.charAt(i))-shift+key.length) % key.length
      link += (key.charAt(ltr))
    }
  }
document.write("<a href='mailto:"+link+"'>take advantage of</a>")
}
//-->
</script><noscript>take advantage of</noscript>. :wink:

### It's actually "Salesforce Analytics Cloud, powered by Wave"
My guess is Benioff got a little too excited by the name at Dreamforce '14, and now everyone thinks it's "Salesforce Wave"... The giant inflatable surfboard made it all worth it though!

<img src="http://dreamforcenews.salesforce.com/sites/dfnews.newshq.businesswire.com/files/image/image/Marc_Keynote_003.JPG" alt="Benioff Dreamforce 14"/>

