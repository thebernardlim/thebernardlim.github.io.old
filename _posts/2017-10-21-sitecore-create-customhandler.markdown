---
layout: post
title:  "Adding Custom Handler in Sitecore"
date:   2017-10-21 15:53:00
categories: sitecore
excerpt : Steps on how to add a custom handler in a Sitecore solution
excerpt_seperator: 
---

Adding custom handlers is a common practice in ASP.Net applications.
Handlers are usually used to receive HTTP requests, does the logic it requires and send back the required response.

Recently, I had to implement one for a form post in Sitecore.
Here are the steps:

1. Under your *Sitecore Web Application* solution, create your handler file. For example in our case, lets name it **Formhandler.ashx**

2. Under **App_Config** folder, in the respective **'Include_yoursite.config'** file, add the following under \<customHandlers>:

```
\<customHandlers><br/>
\<handler trigger="/~/yoursite/formhandler" handler="FormHandler.ashx" /><br/>
\</customHandlers>
```
3. In **'Web.Config'**, add the following under \<handlers>:

```
\<handlers><br/>
\<add verb="*" path="FormHandler.ashx" type="yournamespace.FormHandler" name="FormHandler"/><br/>
\</handlers>
```

4. The handler can now be accessed by the following URL:<br/>
*{your website URL}/FormHandler.ashx*

5. Use a handy tool like [Postman](https://www.getpostman.com/postman) to test out before going into integrating with your code. Ensure that your handler is actually setup properly before start coding. 

