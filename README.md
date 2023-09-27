# Design Principles
The work we do at NUM differs to the traditional tech model, where setup costs are low (or zero) and subscription costs creep up as your use and reliance upon the technology increases. The costs for our work are significantly front-loaded, because we're building an asset for _your_ business, not ours. You could look at it as comparable to owning premises vs renting them.

## No Lock-in
Your ownership of the technology, and its complete independence of any third party lock-in, is the foremost design principle of the technology we build. 

You are free to decide:

- Who maintains your technology (fixing bugs, updating content)
- Who grows it (new projects and features) 
- Who hosts it

Of course, we'll happily take care of it all for you, but that should be your choice.

## Building an Asset
The technology we build should be something that:

- you could list as an asset on your balance sheet for a future investor / acquirer
- apply for R&D corporation tax relief on
- apply for grants for

Our model is the opposite of a third party plugin model, which is usually considered a liability in the sense that it's both a cost and a business critical dependency controlled by a third party.

## Transferrability
We're committed to supporting the technology we build but it's important you have control over it in case of unforeseen circumstances or if you need someone else to take over the management of it at some point in the future. The following sections are a summary of how our technology is usually designed and the providers we use, to ensure the technology is future proof and transferrable. This content is best suited to technical eyes but something we can happily talk clients through.

Our first step in taking on a client is usually to register a domain name on their behalf. This enables us to setup an independent email address (not one we control), and means we don't have to nag you endlessly for verification links, auth codes etc. All accounts with providers are setup in your name / company name using the new email address – we provide you with access to this email address once the work is complete. All credentials are stored in a password manager vault that you have access to once the work is complete.

### Domain Name Registration and DNS: Cloudflare
The domain name is registered via Cloudflare Registrar, DNS is with Cloudflare and the email address we setup for you is also managed by Cloudflare (just a simple email forwarding address).

The ongoing cost of this, is **£10-15 per year**, the first year is included in the setup cost.

### Code Repository: Github
All code is available in an independent organisation on Github (a company owned by Microsoft), this means that anyone that you bring into help in the future can access the code and make changes. There is a private repository for each project we take on for you, each with three environments represented by branches in each project repository:

- development (for us to develop features)
- staging (for you to preview changes before going live, and for us to test features against real data)
- production (what your customers see)

Github make **no charge for this level of usage**.

### Hosting: Heroku
Each repository branch is automatically deployed to Heroku (a company owned by Salesforce).

The standing running costs of this will be **around £150 per year**, with the first year included in your setup costs. Costs will scale as customer use scales but due to the way the technology is built, your running costs should be low even if you're getting tens of thousands of users per day.

### Telephony: Twilio (AI Assistant only)
The number we use for the assistant (via Whatsapp and sometimes SMS) is registered through Twilio, it simply routes messages through the assistant HTTP end points.

The cost of the number is less than **£15 per year** but there are costs to sending messages. WhatsApp pricing is quite complicated because you pay more if you're sending the first message to a contact (e.g. a promotion) and less if you're replying to them (like the Assistant does). You also pay very little for the ongoing conversational messages, after the first message. 

The setup cost includes the first year charge for the number and usually includes a large number of messages.

### AI Model: Open AI (AI Assistant Only)
The assistant typically uses Open AI, although it is built to be switched to other API-based models relatively simply.

The cost of this will depend on customer use, the setup cost usually includes a large number of messages.

## Solid Technology Choices
All of our technology choices are made with the following priorities:

- stability and security: mature technologies
- independence: no CDNs or references to third party scripts
- portability: if you were to have problems with any of the providers above, you could switch to another relatively easily

Websites, web apps and assistants are typically written in the Python programming language, use the Flask web framework and flat file JSON storage. These technologies are incredibly popular and well-known, and you will have no problem finding someone skilled in these technologies if you would like someone else to take over the project further down the line.

# Contact Manager
All customers get access to our Contact Manager tool for the purposes of:

- Content Management System (CMS)
- Customer Relationship Management (CRM)

You can use the Contact Manager to update your website content – e.g. products, services, locations, blog posts and FAQs (the CMS part) and the Contact Manager is used for listing contacts and logging assistant conversations with contacts (the CRM part). However, it's important to note that neither your website nor assistant are reliant on our Contact Manager or dependent on the service to function – if the Contact Manager was unavailable on a short term or long term basis, both would be unaffected:

- Website: The Contact Manager CMS simply writes flat data files (JSON) to your website repository which are then used to generate the content for your website, it is not involved whatsoever in answering web requests
- Assistant: It makes "fire and forget" API calls to the Contact Manager CRM, to log contacts and messages but these are not blocking calls and all conversation data is stored locally

We provide you with the Contact Manager to make CMS and CRM easy and user-friendly,  but if the Contact Manager was down or ceased to exist, the content of your website can be edited using the flat data files and the work of the assistant can be viewed via logs. It would be relatively simple for someone to build an independent interface to manage/view this data (in case Contact Manager was unavailable) and if it was important to you from the start, we could even do this as a mini project at relatively low cost.

# More Avanced Work
For more advanced work, it's likely that it will require closer integration with our Contact Manager tool (for example an assistant to book/manage appointments), where the Contact Manager will be become an integral part of the process and inevitably certain functionality will be reliant on the Contact Manager. However, this dependence will always be made clear and in cases where the work we're doing could be for the benefit of other Contact Manager users (e.g. appointment management), this will also be factored into the price.

# Documentation
As each project is completed and signed off, it will be documented comprehensively in the code repository so that someone can pick it up relatively easily in the future. 
