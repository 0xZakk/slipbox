# How To Build A Marketplace with No Code

Type: #[[📥 Inbox]] #[[📝 To Process]]
Source: https://www.slideshare.net/nocodeconf/how-to-build-a-marketplace-without-code-no-code-conf-2019-workshop
Author: Connor Finlayson
Domain: [[No code]] [[Startups]]

---
**Summary:**

This slide deck explains how to build a market place using no-code tools. The front-end of the market place is all done using Webflow, using Memberstack to hide some content. All data related to the market place is stored in Airtable. Zapier is used to wire everything together and make it all work.
	
---
**Highlights:**

[Unicorn Factory](www.unicornfactory.nz)- A marketplace that connects freelancers and business owners in New Zealand

History:
- Nov 2015 - created apps for local business
- May 2016 - Start referring work to freelancers and other startups
- Feb 2018 - Built prototype for Unicorn Factory

## No Code Setup

Features:
- Automated on-boarding process (with review)
- Automated comms with clients and freelancers (with review)
- Tiered memberships for freelancers
- Metrics & Reporting dashboard in [[Airtable]]
- Users can update their profile

Stack:
- [[Webflow]]: Front-end build of the website
- [[Airtable]]: No-code database
- [[Memberstack]]: Gated content and monetization
- [[Zapier]]: Workflow automation

## How It's Built

**Webflow**
Pages are built in Webflow (ie the profile template for freelancers). These are linked to other CMS collections (like case studies or skills). Custom contact form for each profile page. listings page for categories.

Pages integrate schema.org into the CMS collection pages to generate rich text on Google and for SEO.

**Monetizing with Memberstack**
Create pages in Webflow and use Memberstack to hide them if someone doesn't have an account. Paying freelancers get access to additional features and pages.

**Everything is wired together with Zapier.**

### Processes

**Submitting an inquiry**
- Client submits an inquiry form, which creates a record in an Airtable table called Messages.
- Owner selects the "approve" checkbox which moves the message into an Approved Messages view on Airtable and sends the inquiry to the freelancer

**Freelancer Applications**
- Freelancer completes and application which is submitted to an Airtable
- Owner reviews the application. If it's approved they click Approve which automatically creates an item in a Webflow CMS collection. Owner updates the CMS item ID and slug (has to be done manually)
- Then publishes the profile to the website and send them a welcome email and posts their profile to twitter

## Tips

Start building the pages in Webflow. Then integrate Memberstack to hide pages. Setup Airtable to collect all information. Share with the community.



