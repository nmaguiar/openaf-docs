---
layout: default
title: Sending emails from oJob
parent: Medium
grand_parent: Guides
---

# Sending emails from oJob

Sending emails from oJob is made easy due to the oJobEmail.yaml include from the [oJob-common opack](https://github.com/OpenAF/oJob-common). As we other common ojobs the idea is to be easy to use. Let's look at a very simple example:

````yaml
ojob:
  opacks:
    - oJob-common

include:
  - oJobEmail.yaml

jobs:
  # -----------------------
  - name: Send a test email
    to  : oJob Send email
    args:
      from       : "my.email@gmail.com"
      server     : "smtp.gmail.com"         # for example
      credentials:
        user: "my.email@gmail.com"
        pass: "myAppPassword"
      useSSL     : true
      useTLS     : true
      to         : "someone@somewhere.com"
      subject    : "My test email"
      output     : "This is a test email to test sending emails from oJob"
      debug      : false

todo:
  - Send a test email
````

This example will send an email from my.email@gmail.com to someone@somewhere.com with a test subject a email message. 

## SMTP server settings

Depending on the SMTP email servers you might need to use different settings:

| Setting | Type | Default | Description |
|---------|------|---------|-------------|
| *useSSL*  | boolean | false | If the SMTP connection should use SSL (can use also TLS). |
| *useTLS*  | boolean | false | If the SMTP connection should use TLS (can use also SSL). |
| *port*    | number | 25/587/465 | Specify the port to contact the SMTP server. |
| *server*  | string | | The server address. |
| *credentials* | map | | A map with user and pass to use to authenticate on SMTP servers. |
| *debug* | boolean | false | Very useful to debug SMTP connections by showing all the communication between oJob and the SMTP server. |

## Email basic settings

For the email specifics you can see in the example the use of the from, to, subject and output fields. The other possible fields are also the obvious:

| Setting | Type | Description |
|---------|------|-------------|
| *from* | string | A string representing the "from" address. |
| *to* | string/array | An array or a string of "to" addresses. |
| *cc* | string/array | An array or a string of "cc" addresses. |
| *bcc* | string/array | An array or a string of "bcc" addresses. |
| *subject* | string | The text subject of the email message. |
| *output* | string | The text message of the email message. |
| *isHTML* | boolean | Specifies, if true, that the output is in HTML format. |
| *altOutput* | string | If isHTML = true and the end client doesn't support HTML this will be the alternative output to show. |

## Sending attachments

To send any file as an attachment just use "addAttachments":

````yaml
      addAttachments:
        - name    : file.txt
          file    : /some/path/file.txt
        - name    : secondFile.txt
          file    : /some/path/secondFile.txt
````

## Adding images to HTML emails

You have three options:

### Embed image URLs

````yaml
      isHTML   : true
      output   : "<html>...<img src=\"cid:myimage\"/>...</html>"
      embedURLs:
        - name: myimage
          url : https://some.server/some/image.jpg
````

### Embed image files

````yaml
      isHTML        : true
      output        : "<html>...<img src=\"cid:myimage.png\"/>...</html>"
      embedFiles:
        - name    : myimage.png
          file    : /some/path/myimage.png
````

### Automatic embedding images and reference them by URL

````yaml
      isHTML   : true
      output   : "<html>...<img src="https://some.server/some/image.jpg"/>...</html>"
      addImages:
        - https://some.server/some/image.jpg
````