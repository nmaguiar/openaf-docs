---
layout: default
title: email
parent: Reference
grand_parent: OpenAF docs
---


## email

### Email.addAttachment

__Email.addAttachment(aPath, isInline, noDisposition, aName) : Email__

````
Adds aPath file as an attachment for the current email. Optionally you can specify if it's an inline (isInline) attachment; noDisposition = true to not set it as inline or attachment (ignores isInline); an internal aName.
````
### Email.addAttachment

__Email.addAttachment(aPath, isInline, noDisposition, aName) : Email__

````
Adds aPath file as an attachment for the current email. Optionally you can specify if it's an inline (isInline) attachment; noDisposition = true to not set it as inline or attachment (ignores isInline); an internal aName.
````
### Email.addBcc

__Email.addBcc(aBccOrList) : Email__

````
Sets the current email bcc email address or an array of bcc email addresses.
````
### Email.addBcc

__Email.addBcc(aBccOrList) : Email__

````
Sets the current email bcc email address or an array of bcc email addresses.
````
### Email.addCc

__Email.addCc(aCcOrList) : Email__

````
Sets the current email cc email address or an array of cc email addresses.
````
### Email.addCc

__Email.addCc(aCcOrList) : Email__

````
Sets the current email cc email address or an array of cc email addresses.
````
### Email.addExternalImage

__Email.addExternalImage(aURL) : Email__

````
Retrieves an external image from aURL and set's everything for that URL to be used in HTML.  Only available if the Email object was initialized with isHtml = true.
````
### Email.addExternalImage

__Email.addExternalImage(aURL) : Email__

````
Retrieves an external image from aURL and set's everything for that URL to be used in HTML.  Only available if the Email object was initialized with isHtml = true.
````
### Email.addHeader

__Email.addHeader(aKey, aValue) : Email__

````
Add a SMTP header with aKey and the corresponding aValue.
````
### Email.addHeader

__Email.addHeader(aKey, aValue) : Email__

````
Add a SMTP header with aKey and the corresponding aValue.
````
### Email.addHTMLHeader

__Email.addHTMLHeader() : Email__

````
(deprecation) Please use the option in the constructor and the setHTML function. Adds the necessary headers to support HTML contents.  To be deprecated in the future. Please use new Email with isHTML = true and the setHTML function.
````
### Email.addHTMLHeader

__Email.addHTMLHeader() : Email__

````
(deprecation) Please use the option in the constructor and the setHTML function. Adds the necessary headers to support HTML contents.  To be deprecated in the future. Please use new Email with isHTML = true and the setHTML function.
````
### Email.addTo

__Email.addTo(aToOrList) : Email__

````
Sets the current email "To" email address or an array of "To" email addresses.
````
### Email.addTo

__Email.addTo(aToOrList) : Email__

````
Sets the current email "To" email address or an array of "To" email addresses.
````
### Email.email

__Email.email(aServer, aSenderAddress, shouldSecure, useTLS, isHTML)__

````
Creates a Email object instance using the aServer SMTP server to send email with the from field set to aSenderAddress. Optionally you can specify if a secure protocol (SSL) should be used with shouldSecure = true, to TLS add shouldSecure = true and useTLS = true and isHTML to use the setHTML function later.
````
### Email.email

__Email.email(aServer, aSenderAddress, shouldSecure, useTLS, isHTML)__

````
Creates a Email object instance using the aServer SMTP server to send email with the from field set to aSenderAddress. Optionally you can specify if a secure protocol (SSL) should be used with shouldSecure = true, to TLS add shouldSecure = true and useTLS = true and isHTML to use the setHTML function later.
````
### Email.embedFile

__Email.embedFile(aFilePath, aName) : Email__

````
Tries to embed aFilePath with aName and returns the cid to be used in HTML (e.g. img src="cid:xxx").  Only available if the Email object was initialized with isHtml = true.
````
### Email.embedFile

__Email.embedFile(aFilePath, aName) : Email__

````
Tries to embed aFilePath with aName and returns the cid to be used in HTML (e.g. img src="cid:xxx").  Only available if the Email object was initialized with isHtml = true.
````
### Email.embedURL

__Email.embedURL(aURL, aName) : Email__

````
Tries to embed aURL with aName and returns the cid to be used in HTML (e.g. img src="cid:xxx").  Only available if the Email object was initialized with isHtml = true.
````
### Email.embedURL

__Email.embedURL(aURL, aName) : Email__

````
Tries to embed aURL with aName and returns the cid to be used in HTML (e.g. img src="cid:xxx").  Only available if the Email object was initialized with isHtml = true.
````
### Email.getEmailObj

__Email.getEmailObj() : JavaObject__

````
Returns the internal Java object used to composed the email message for advance usage. See more in https://commons.apache.org/proper/commons-email/apidocs/org/apache/commons/mail/Email.html.
````
### Email.getEmailObj

__Email.getEmailObj() : JavaObject__

````
Returns the internal Java object used to composed the email message for advance usage. See more in https://commons.apache.org/proper/commons-email/apidocs/org/apache/commons/mail/Email.html.
````
### Email.login

__Email.login(aLogin, aPassword)__

````
Sets the credentials to use when using a SMTP server which activates the use of a secure protocol (TLS/SSL) if available.
````
### Email.login

__Email.login(aLogin, aPassword)__

````
Sets the credentials to use when using a SMTP server which activates the use of a secure protocol (TLS/SSL) if available.
````
### Email.send

__Email.send(aSubject, aMessage, aToList, aCCList, aBCCList, aSender) : String__

````
Sends an email with aSubject and aMessage to the provided array of aToList, aCCList and aBCCList. Optionally you can specify a from address in aSender, otherwise the default for this object instance will be used. Returns the id of the message sent.
````
### Email.send

__Email.send(aSubject, aMessage, aToList, aCCList, aBCCList, aSender) : String__

````
Sends an email with aSubject and aMessage to the provided array of aToList, aCCList and aBCCList. Optionally you can specify a from address in aSender, otherwise the default for this object instance will be used. Returns the id of the message sent.
````
### Email.setCharset

__Email.setCharset(aCharset) : Email__

````
Sets the current email aCharset to use.
````
### Email.setCharset

__Email.setCharset(aCharset) : Email__

````
Sets the current email aCharset to use.
````
### Email.setContent

__Email.setContent(aContent, aContentType) : Email__

````
Sets the current email body message to send with aContent string. Specifies also that the corresponding  content type is aContentType.
````
### Email.setContent

__Email.setContent(aContent, aContentType) : Email__

````
Sets the current email body message to send with aContent string. Specifies also that the corresponding  content type is aContentType.
````
### Email.setCredentials

__Email.setCredentials(aLogin, aPassword)__

````
Sets the credentials to use when using a SMTP server which activates the use of a secure protocol (TLS/SSL) if available.
````
### Email.setCredentials

__Email.setCredentials(aLogin, aPassword)__

````
Sets the credentials to use when using a SMTP server which activates the use of a secure protocol (TLS/SSL) if available.
````
### Email.setFrom

__Email.setFrom(aFrom) : Email__

````
Sets the current email aFrom email address.
````
### Email.setFrom

__Email.setFrom(aFrom) : Email__

````
Sets the current email aFrom email address.
````
### Email.setHTML

__Email.setHTML(aHTML) : Email__

````
If the Email object was initialized with isHtml = true then will set the HTML content to aHTML.
````
### Email.setHTML

__Email.setHTML(aHTML) : Email__

````
If the Email object was initialized with isHtml = true then will set the HTML content to aHTML.
````
### Email.setMessage

__Email.setMessage(aMessage) : Email__

````
Sets the current email body message to send (raw). Please use Email.setContent to specify the mime type. For  emails initialized with isHtml = true, sets the alternative text content to show.
````
### Email.setMessage

__Email.setMessage(aMessage) : Email__

````
Sets the current email body message to send (raw). Please use Email.setContent to specify the mime type. For  emails initialized with isHtml = true, sets the alternative text content to show.
````
### Email.setPort

__Email.setPort(aPort)__

````
Sets aPort to contact the SMTP server.
````
### Email.setPort

__Email.setPort(aPort)__

````
Sets aPort to contact the SMTP server.
````
### Email.setSubject

__Email.setSubject(aSubject) : Email__

````
Sets the email's aSubject;
````
### Email.setSubject

__Email.setSubject(aSubject) : Email__

````
Sets the email's aSubject;
````
