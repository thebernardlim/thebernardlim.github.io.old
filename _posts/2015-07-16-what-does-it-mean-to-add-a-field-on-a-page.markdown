--- 
layout:	post
title: 	"What does it ACTUALLY mean to just add JUST ONE field to an existing page"
date:	2015-07-16 00:19:00
categories:	software-development
excerpt: A harmless request of `adding a simple field to an existing page` cannot be that complex right? This post explores dives in and explores what actually goes through a client's and dev's mind in such a scenario.
---

This is a pretty common scenario for any programmers/devs:

Client 	:	I have a quick change request for our user checkout page. <br/>
Dev	 	:	Cool, what is it? <br/>
Client 	:  Just a simple text field for users to enter how they found out about our website <br/>
Dev	 	:	&#42; *Pauses and thinks* &#42; <br/>
Client 	: 	We reckon its a quick change and would want it asap . How long would this require <br/>
Dev	 	: 	&#42; *Calculates and decides* &#42; 2 weeks <br/>
Client 	:	&#42; *Stunned, expecting only a couple of days max* &#42; Could you reconsider dev time, and see if we can release it earlier? <br/>

...

## What clients usually thinks in such a scenario 

- I've played with Dreamweaver before. Its just a drag and drop. Right-click bind to database. BAM Done!
- Okay, maybe it is different in post-Dreamweaver days. Ah, but they are a 1001 spoon-feeding frameworks nowadays. Should be easy peasy.
- Users will be happy and we can get info of where visitors were referred from
- Higher investment towards whatever worked from the above info obtained
- More $$$

## What a developer thinks in such a scenario

### WHY

This is the main question a dev will ask themselves (if they haven't got it from the clients yet). At this point, devs will roughly try to figure from the client's perspective on why this feature was requested.

In the above scenario, he/she had already said "how they found out about the website" isn't it?
Yes and No.

Yes - To the purpose of the field in **page** context <br/>
No  - To the purpose of the field in **business/site** context.

But why would devs want to bother with the business/site context? We are only devs, not the clients.

Simple, we were hired to develop your product to ULTIMATELY meet your business goals at the end of the day!

More to be explained below, on why we need to understand the whole context.

### WHERE

This should be a simple question. Drag the field to wherever the client requested it. Matter of seconds. 

WRONG. Totally.

Why? UI Heuristics, mate! Though, UI is not definitely most developers' strengths, most of us the are from a CS background have probably been grounded in module or two involving UI heurestics (Yep Jakob Nielsen) or any devs actually worth their salt should have read an article or two about importance of UI design guidelines or purely from client/user feedbacks from projects of the past.

Is this significant? Definitely. An improperly placed field will probably defeat the initial purpose of the new field! Imagine out of 5000 users, only 1000 users actually keyed in, while the remaining 4000 missed out because it was small and place way below the huge 'Checkout' button. 

### HOW

Drag and drop, right-click bind to new column in database table.

Well, top-level view, that is correct. 

A more precise explanation on what actually happens:


- Drag and drop from UI toolbar

To figure out storing field info:


- Explore database to decide where the data from this new field will go in
- Create new column in that specific table? Run table through basic ER diagram rules. Any redundancy for this new column? Is this column mandatory? Any impact on existing data? Or do we actually need a new table with foreign key as User ID?
- Will control be a mandatory field? Any other client-side validations? Max/Min length limits? Any other restrictions?
- Any events required for this field? Call server when user leaves field? Or AJAX call? 
- Any other behaviors? Only show field when user successfully keyed in credit card number? Highlight field in red bordered box?
- Is behavior of this newly introduced field consistent with the whole site/page? Suddenly an AJAX field when the whole site requires post-back?
- Data Access layer not inviting SQL Injection? 
- Wait, or maybe we can use some other alternative controls? Dropdowns, radio buttons, checkboxes if require user to choose from pre-selected values. Can user select 1 or multiple values? 
- If pre-selected values, we will need a place to store these values. New db table? Config file?

Then.. how will user retrieve the data?


- New page with Charts? Tables? Any sort fields? Search feature? 
- Access rights for page? Can pre-use existing user access groups?
- Modify stored procedure to retrieve new value? In-code merge? New data structure required?

### WHEN

Usually probably the last priority in terms of the thought process if user did not emphasize on the timeframe given pre-meeting. Usually calculated through experience or a proper estimate calculator (through mandays, hours etc). 

What is involved?

- Dev Setup
- Build time
- Documentation
- Unit testing, regression testing
- Deployment, migration activities


Add onto it an extra **BUFFER** period.

Wait, what buffer? Clients want it asap already!

Buffer is almost one of the most important skill in software dev estimation for any dev, because there is so much trial and error, bug fighting/fixing and other roadblocks / showstoppers along the way from dev to releasing something live. Little niggles like a sudden browser upgrade, framework upgrade, or something even worse like fixing someone else's legacy system, could easily mean Googling for days, or taking extra time to re-setup your dev environment to reading up and trying to understand boring API docs. All these take up valuable time that we can predict before the start of a dev process.

On top of buffer, why is this given the final worry in a dev's thought process?
Simple, failing to understand a client's requirements properly would mean total failure irregardless it takes 5 mins or 5 years to implement. 

End goal of any dev project is to build something to meet client's goal within optimum timeframe as agreed by both parties. 



##Conclusion

Adding a field is not a straightforward process! Though for some cases it could be, say for example a non-mandatory field in a low-impact page. Hence always practice extra caution when users/clients want a **SIMPLE** change! Chances are there are more to it!

I hope I had given an informative insight from a dev's point of view on what really goes through our think process when we hear 'a simple request' from a client.

