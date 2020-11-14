---
layout: default
title: Executing code when an OpenAF script execution is terminated
parent: Medium
grand_parent: Guides
---

# Executing code when an OpenAF script execution is terminated

Usually there is a need to execute specific code whenever a script is ending/shutting down. Either by normal or forced termination. Examples of this are closing connected sessions to other servers (e.g. databases), deallocate used resources, etc&#49;&#49;&#49;

In OpenAF this can be achieved using addOnOpenAFShutdown:

````javascript
addOnOpenAFShutdown(function() {
   // Some closing code
   // ...
});
````

The following example closes the created mini web server upon normal or forced termination:

````javascript
ow.loadServer();
 
// Setting up
!pidCheckIn("testserver.pid") && !log("Already running") && exit(0);
// Add code to execute on termination
addOnOpenAFShutdown(function() {
   log("Stopping...");
   hs.stop();
   log("Done!");
});
 
// Starting the httpd server
log("Starting...");
 
var hs = ow.server.httpd.start(8888);
hs.add("/", function(r) {
   return hs.replyOKText("Current date: " + new Date());
});
 
log("Ready");
 
// Converting the script into a daemon so that it doesn't terminate upon Ctrl-C or similar
ow.server.daemon();
````
Do note that every call to addOnOpenAFShutdown will add a new hook. Upon termination, the last added hook will be the first to be executed and backwards to the first added.