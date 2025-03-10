# Building a simple web-service to run a command-line

_(OpenAF version >= 20241117)_

Using oJob shortcuts it's easy to quickly deploy a testing web-service. Let's suppose you need to run script _my-script.sh_.

Write a "server.yaml":

```yaml
init:
  port: &PORT 8081

todo:
- (httpdStart  ): *PORT
- (httpdDefault): *PORT
- (httpdService): *PORT
  ((uri       )): /run_script
  ((execURI   )): |
    // The command to run
    var cmd = "/some/path/my-script.sh"

    // Running the command
    var res = $sh(cmd).get(0)
    
    // Examines the exit code of the command
    if (res.exitcode != 0) {
      // If exit code not zero return HTTP 500 error
      return ow.server.httpd.reply("Execution error", 500)
    } else {
      // If script runs successfully return the correspoding stdout and stderr
      return ow.server.httpd.reply({ out: res.stdout, err: res.stderr }, 200)
    }

include:
- oJobHTTPd.yaml

ojob:
  opacks      :
  - openaf     : 20241117
  - oJob-common: 20250126
  catch       : printErrnl("[" + job.name + "] "); if (isDef(exception.javaException)) exception.javaException.printStackTrace(); else printErr(exception)
  logToConsole: true   # to change when finished
  daemon      : true
```

To start it, execute:

```bash
ojob server.yaml
```

To test it, just execute:

```bash
curl http://my.host.name:8081/run_script
```