# Sending emails

The OpenAF included plugin Email allows to easily send emails from any OpenAF script. Let's check it using a simple example:

````javascript
plugin("Email");
var email = new Email("smtp.gmail.com", "my.email@gmail.com", true, true, false);
email.login("my.email@gmail.com", "myAppPassword");
email.send("Something is wrong", "Something was detected to be very wrong.", [ "someone@somewhere.com" ], [], [], "my.email@gmail.com");
````

## Step by step

Let's translate each line. After including the plugin Email we created a new Email instance for the SMTP server "smtp.gmail.com" for the email account "my.email@gmail.com", turned SSL and TLS on and specified the email wasn't going to contain any HTML.

````javascript
// Email(aSMTPServer, theFromEmailAddress, useSSL, useTLS, containsHTML)
var email = new Email("smtp.gmail.com", "my.email@gmail.com", true, true, false);
````

The Email plugin will try to "guess" the right ports to access the SMTP server but if you need to force it you can do it:

````javascript
email.setPort(12345);
````

The next step was authenticating with the SMTP server:

````javascript
email.login(aLogin, aPassword);
````

And then finally we sent the simple email:

````javascript
// email.send(aSubjectString, aMessageString, anArrayOfTOs, anArrayOfCCs, anArrayOfBCCs, aFromEmailAddress)
email.send("Something is wrong", "Something was detected to be very wrong.", [ "someone@somewhere.com" ], [], [], "my.email@gmail.com");
````

## How to send a HTML email

To send a HTML email first you will need to specify it on the Email instance creation:

````javascript
var email = new Email("smtp.gmail.com", "my.email@gmail.com", true, true, true);
````

Afterwards you add the HTML using the .setHTML function:

````javascript
email.setHTML("<h1>BIG NEWS</h1>Everything is <b>okay</b>.");
````

So, if we just defined the email contents why should we defined _aMessageString_ on the _email.send_ function? In case the email client doesn't support HTML emails the aMessageString parameter of the _email.send_ function will be used.

## Adding attachments

To add an attachment use the function _email.addAttachment_:

````javascript
email.addAttachment("/my/folder/with/attach1.pdf");
````

## Adding images for the HTML content

If you use HTML content you will probably also want to include images. These aren't the usual regular attachments and there is actually 3 options available:

### Embed image files

````javascript
email.setHTML("<html>...<img src=\"cid:myimage.png\"/>...</html>");
email.embedFile("/some/path/myimage.png", "myimage.pn");
````

### Embed image URLs

````javascript
email.setHTML("<html>...<img src=\"cid:myimage\"/>...</html>");
email.embedURL("https://some.server/some/image.jpg", "myimage");
````

### Automatic embedding images and reference them by URL

````javascript
email.setHTML("<html>...<img src="https://some.server/some/image.jpg"/>...</html>");
email.addExternalImage("https://some.server/some/image.jpg");
````

## How to debug

After creating the new Email instance just add:

````javascript
email.getEmailObj().setDebug(true);
````

Once the email sending operation starts all communication with the SMTP server will be output to stdout/stderr.