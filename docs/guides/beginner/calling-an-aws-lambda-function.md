---
layout: default
title: Calling an AWS Lambda function
parent: Beginner
grand_parent: Guides
---

# Calling an AWS Lambda function

If you have an AWS Lambda function that you need to call from OpenAF you can use the [AWS oPack](https://github.com/OpenAF/openaf-opacks/tree/master/AWS). You can call it from within an AWS network or from the Internet (e.g. with the appropriate permissions). To install the AWS oPack execute:

````bash
$ opack install aws
````

To use the AWS functionality programmatically you will need an AWS API KEY and an AWS API Secret (check the [setup instructions](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey) in AWS). Keep in mind that the API Key + Secret you will need to have the necessary permissions to execute AWS Lambda functions.

## Example

Let's call a simple AWS Lambda function:

````javascript
loadLib("aws.js");
var aws = new AWS(apiKey, apiSecret); // replace or define string variables with the corresponding AWS API Key & Secret

var res = aws.LAMBDA_Invoke("eu-west-1", "test");
sprint(res); // Print the result

// The variable res will have something similar to:
// {
//  "statusCode": 200,
//  "body": "\"Hello from Lambda!\""
//}
````

To pass arguments just add the input map:

````javascript
loadLib("aws.js");
var aws = new AWS(apiKey, apiSecret); // replace or define string variables with the corresponding AWS API Key & Secret

var res = aws.LAMBDA_Invoke("eu-west-1", "addAPlusB", { a: 2, b: 3 });
sprint(res); // Print the result

// The variable res will have something similar to:
// {
//    "a": 2,
//    "b": 3,
//    "result": 5
// }
````

## Calling an AWS Lambda asynchronously

To call an AWS Lambda asynchronously continuing the OpenAF execution without waiting for a result just use the function LAMBDA_InvokeAsync:

````javascript
loadLib("aws.js");
var aws = new AWS(apiKey, apiSecret); // replace or define string variables with the corresponding AWS API Key & Secret

aws.LAMBDA_InvokeAsync("eu-west-1", "test");
````

It's also possible to use OpenAF as an AWS lambda language using the [OpenAFLambdaLayers opack](https://github.com/OpenAF/openaf-opacks).