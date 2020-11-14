---
layout: default
title: Check if an email address is valid for sending emails
parent: Medium
grand_parent: Guides
---

# Check if an email address is valid for sending emails

Whenever you have a list of email addresses you might wonder if the email address provided really exists or if it's a "dummy" email. Since internet email does not provide any delivery guarantees nor there exists any reply standard (or obligation) from target domains to reply back that the email address does not exist what can you check to clean cases like "my.name@you.wont.find.me" automatically?

The options are:
  * Find if the domain really exists
  * Find if the domain has any email servers associated

Both can easily be checked by performing DNS lookups. Most operating systems provide the command "nslookup" to easily lookup this information.

_Note: There are several types of entries in DNS records. For example the entry type "A" means the IP4 address associated with the domain record while "MX" means the email server associated with the domain record._

An easy way to implement this is to use the [Google Public DNS-over-HTTPS service](https://developers.google.com/speed/public-dns/docs/dns-over-https). This allows you to easily retrieve the info needed throw a public REST call.

Here is an example of usage in OpenAF scripting:

````javascript
function(checkEmail) {
   var dom = email.split(/@/)[1]; 
   var res = $rest({ uriQuery: true })
             .get("https://dns.google.com/resolve", { 
                name: "gmail.com", 
                type: 255 
             });
 
   return { 
      exists: isDef(res) && isDef(res.Answer),
      hasMXRecords: (isDef(res.Answer)) 
                      ? $from(res.Answer).equals("type", 15).any()
                      : false
   } 
}
````

Executing this function for some examples (valid at the time of writing):

````javascript
// goo.gl is a google url shortener service, it exists but no emails can't be sent to it
> checkEmail("abc@goo.gl") 
{
   "exists": true,
   "hasMXRecords": false
}
 
// gmail.com exists and emails can be sent to it
> checkEmail("abc@gmail.com") 
{
   "exists": true,
   "hasMXRecords": true
}
 
// miguel.com is a domain bought to be resold but doesn't have a site nor email can be sent to it
> checkEmail("abc@miguel.com")
{
   "exists": false,
   "hasMXRecords": false
}
 
// nuno.com is a japanese textil company, so the domain exists and emails can be sent to it
> checkEmail("nuno@nuno.com")
{
   "exists": true,
   "hasMXRecords": true
}
 
// finally, my.name@you.wont.find.me (yes, it exists and it's a site)
> checkEmail("my.name@you.wont.find.me")
{
   "exists": true,
   "hasMXRecords": false
}
````