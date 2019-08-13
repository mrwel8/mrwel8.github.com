---
published: true
layout: post
date: '2019-01-02'
comments: true
permalink: continuous-delivery-salesforce
title: Baby Steps in Continuous Delivery for Salesforce
---
_Taking on the DevOps boss in 9 levels_

> This post was first published on the <a href="https://medium.com/slalom-technology/baby-steps-in-continuous-delivery-for-salesforce-1973fc651803" target="_blank">Slalom Technology blog</a>.

Of all the elements that every Salesforce project contains, the most underrated one has to be the deployment process. Sure, getting the work done in a timely and accurate way is the ultimate goal, but if you can’t get it into production, _who cares?_

After spending a Sunday evening fixing a P1 bug and looking at one too many <a href="http://scottvonschilling.com/2015/11/23/for-the-love-of-deploymentfish/" target="_blank">deployment fish</a>, I decided enough was enough. What could I do to guarantee that any push to production was simple and error-free? Down the internet rabbit hole I went, deep into the world of DevOps.

Turns out I was late to the party — <a href="https://www.atlassian.com/continuous-delivery" target="_blank">Continuous Delivery</a> was the solution I was looking for, and <a href="https://developer.salesforce.com/blogs/2017/10/salesforce-dx-is-now-generally-available.html" target="_blank">Salesforce DX</a> was built upon its tenets. With “agile” <a href="https://medium.com/slalom-technology/salesforce-agility-in-3-steps-331aa4381b76" target="_blank">in mind</a>, I set about on the journey, one step after the other.

> Continuous Delivery is an approach where teams release quality products frequently and predictably from source code repository to production in an automated fashion.

---

### Level 1: The source of truth
It goes without saying that the most important aspect of any deployment is what exactly is being deployed. <a href="https://help.salesforce.com/articleView?id=changesets.htm&type=5" target="_blank">Change Sets</a> do this well — All components are listed in one view that can be paged through 200 rows at a time. But what if one of those components or one of its dependents is currently being worked on by someone else? What about when you’re actually ready to deploy only to be told “<a href="https://www.reddit.com/r/salesforce/comments/8xhb63/change_set_to_nowhere/e23j2nu" target="_blank">Change Set Unavailable</a>”? Also, wouldn’t it be nice to see the entire “who-when-what” history of, say, a page layout?

That’s where source control comes in. Just like any of the safe & versionable document storage systems we’re all used to (SharePoint, Dropbox), all the work done on any Salesforce org should be immediately available and up-to-date with the customizations and code that other folks are working on.

To start off, let’s grab everything from an org and save it (also known as “retrieve” or “pull down”). Logically, there are only 3 steps involved, and each corresponds to one command in either the <a href="https://developer.salesforce.com/docs/atlas.en-us.sfdx_setup.meta/sfdx_setup/sfdx_setup_install_cli.htm" target="_blank">Salesforce CLI</a> or <a href="https://help.github.com/articles/set-up-git/" target="_blank">Git</a><a id="link1" href="#quote1">¹</a>:

1. Login: `sfdx force:auth:web:login`
2. Retrieve: `sfdx force:mdapi:retrieve`
3. Save: `git commit`

### Level 2: What comes down must go up
What’s the opposite of retrieving/pulling? Deploying/pushing! Given that the source has everything that needs to be deployed from step 3 above, only two steps are needed here:

1. Login: `sfdx force:auth:web:login`
2. Deploy: `sfdx force:mdapi:deploy`

### Level 3: The party pooper
Now that you’ve drastically simplified the process of retrieving & deploying Salesforce customizations & code, everyone is happy and everything is working in perfect harmony!

Except for that one time.

---

In an effort to delight the business first thing Monday morning, Jake<a id="link2" href="#quote2">²</a> spent all Sunday on a new flow that automatically updates a Contact’s address from its Account. He ran a few tests right around midnight and everything looked good, so he used the brand new process to get it to production in no time at all! Having worked overtime, he decided to set his alarm a little later than usual, and looked forward to a standing ovation when he strolled into work the next morning.

Fast-forward a few hours, and Jake’s supervisor Brianna has 10 urgent emails from the business about users not being able to edit Contacts in Salesforce, and no idea what happened other than Jake’s name being at the top of the Setup Audit Trail. Sound familiar?

---

Whether it’s a point-and-click configuration or a line of code, anyone’s work should always be checked by someone else. To this extent, nearly all source control tools include the concept of a code review in order to have others validate what is being saved.

<img src="/assets/pics/cd-pipeline.png" alt="Diagram of pipeline" style="width: 30%;float: left;"/>

Using <a href="https://bitbucket.org/" target="_blank">Bitbucket</a> as an example, Brianna can prevent any more blunders by requiring Jake to create a pull request any time he wants to change something in the source. From this request, she can easily see what Jake changed and leave comments directly on the component or line that may look wrong. Once the back and forth is complete and Brianna leaves her “<a href="https://medium.freecodecamp.org/what-do-cryptic-github-comments-mean-9c1912bcc0a4" target="_blank">LGTM</a>”, only then can Jake deploy his work to production.

### Level 4: A requirement appears!
In addition to the CLI referenced above, the ability to quickly spin up an environment for any purpose was a significant new feature delivered with Salesforce DX. Instead of having to create a new sandbox from production or go through the Developer org signup form, a scratch org can be setup with test data and users in 3 steps:

1. Create the environment: `sfdx force:org:create`
2. Import test data: `sfdx force:data:tree:import`
3. Create user(s): `sfdx force:user:create`

With this new org, admins and developers alike can then use the steps from Levels 1 and 2 above to deploy and retrieve their work on request. Because of the simplicity of this process, they can also spin up new environments to isolate each and every bug to fix or feature request.

### Level 5: Keeping in touch
As the number of orgs grows and grows, so too does the need to make sure everyone is working on the latest and greatest version of what has been built so far. Although this can be as easy as <a href="https://www.jamesshore.com/Blog/Continuous-Integration-on-a-Dollar-a-Day.html" target="_blank">ringing a bell</a> to let others know when a change was made, technically this problem was already partially solved by Level 2 above — All that needs to be done here is automating it.

The key challenge then can be rephrased as follows: How can a change to the source trigger a set of commands to be run in a specific Salesforce org? Thankfully a number of tools exist that take care of the heavy lifting, and we’ll use Bitbucket <a href="https://bitbucket.org/product/features/pipelines" target="_blank">Pipelines</a> as an example to boil it down to 4 steps:

1. <a href="https://confluence.atlassian.com/bitbucket/configure-bitbucket-pipelines-yml-792298910.html" target="_blank">Create a Pipeline</a> that includes the Salesforce CLI
2. Add the commands from Level 2 (login + deploy)
3. <a href="https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_auth_jwt_flow.htm" target="_blank">Configure</a> the username & Connected App parameters that enable the Pipeline to automatically login to the target org
4. Test it out!

> While this level is likely the most technically challenging, it’s also one of the best documented, with step-by-step instructions for many leading tools including <a href="https://www.youtube.com/watch?v=VlNnDdx1-1E" target="_blank">Bitbucket</a>, <a href="https://trailhead.salesforce.com/content/learn/modules/sfdx_travis_ci" target="_blank">Travis CI</a>, <a href="https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_ci_jenkins.htm" target="_blank">Jenkins</a>, and <a href="https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_ci_circle.htm" target="_blank">Circle CI</a>.

### Level 6: Trust the process
With your first Pipeline now setup, the question is no longer “how” but “what”. In essence, all of the previous levels can be automated in order to create a streamlined end-to-end development process:

1. In one click, admins and devs spin up a scratch org pre-loaded with test data and any ongoing work or historical change
2. After their changes are complete, they are versioned and peer reviewed
3. Once reviewed, the changes are automatically pushed to any org

Looking back on the promise of Continuous Delivery, we’ve therefore achieved the following:

- More dependable releases — Deployments to production can be tested and validated in as many orgs as needed
- More frequent releases — Changes can be deployed on demand and/or automatically
- Less busy work — Time is no longer spent on preparing and setting up deployments

### Levels 7, 8, 9: Quality over quantity
For all the hours and emails saved by setting up code reviews (Level 3), sometimes there are things that mere mortals like Brianna and Jake may miss or simply cannot anticipate. Sure, a thorough QA check of all user workflows wouldn’t let anything slip by, but at what cost?

<img src="/assets/pics/cd-gif.gif" alt="Diagram of pipeline as a gif" style="width: 30%;float: left;"/>

The key to this challenge is **automated testing** which consists of code that can be run on demand, both in the UI and against backend services, to validate that the work being done meets quality standards and does not break existing integrations and user workflows.

Here again, a number of tools (such as <a href="https://www.seleniumhq.org/" target="_blank">Selenium</a>) exist to help build these checks, but it’s important to note that they must reach beyond Apex and Lightning tests, which are not geared towards point-and-click configurations. Nevertheless, even with just a subset of your source covered, the final 3 levels are then within reach:

**7. Continuous Integration**: Run automated tests in one sandbox (commonly called “System Integration Testing”, or “SIT” for short) at least daily

**8. Continuous Integration II** (sometimes also called “Continuous Delivery”): Automate tests and deployments to all sandboxes

**9. Continuous Deployment**: Automate tests and deployments in all sandboxes + production

With the Salesforce CLI here to stay and new features being added <a href="https://developer.salesforce.com/media/salesforce-cli/releasenotes.html" target="_blank">weekly</a>, consider adding it to the New Year’s resolutions for your org — Those deployment fish will do just fine without you!

<p style="text-align: center"><img src="/assets/pics/cd-fish.png" alt="Astro with Deployment Fish" style="width: 30%;"/></p>

---

_<a id="quote1" href="#link1">^¹</a> The commands listed are tailored to non-<a href="https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_scratch_orgs.htm" target="_blank">scratch orgs</a>, such as sandboxes or developer orgs, and are slightly simplified for clarity. For complete details, check out this <a href="https://www.slalom.com/thinking/continuous-integration-in-salesforce" target="_blank">foolproof step-by-step guide</a> and the following Trailhead modules on <a href="https://trailhead.salesforce.com/content/learn/modules/sfdx_app_dev/sfdx_app_dev_setup_dx?trail_id=sfdx_get_started" target="_blank">setting up the Salesforce CLI</a> and <a href="https://trailhead.salesforce.com/content/learn/modules/git-and-git-hub-basics?trail_id=sfdx_get_started" target="_blank">Git basics</a>._

_<a id="quote2" href="#link2">^²</a> Any resemblance to actual persons or actual events is purely coincidental_ 😉

> Thanks to Marty Y. Chang, Keerthana Pachalla, and Venks Pai.
