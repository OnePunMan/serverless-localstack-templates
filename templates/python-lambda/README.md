# Lambda in Python
This template serves as a simple lambda function. It demonstrates how to deploy the function to localstack, AWS, testing it, as well as transforming it to your own.

## Local setup
Hopefully, you went through the initial steps at the top-level [`README.md`](../../README.md) to get here. If not, you will need to go through it to meet all the prerequisites before continuing.

1. Deploying the lambda function to localstack (run in this directory)

    `serverless deploy --stage local`

    with the provided configuration, localstack should automatically boot up deploy your function. If you prefer to always start manually, set `autoStart` and `mountCode` in [`serverless.yml`](serverless.yml) to `false`.

    If successful, serverless will return a result that may look something like this, keep in the mind of the `endpoints` and `functions` result:
    ```
    Service Information
    service: my-service
    stage: local
    region: us-east-1
    stack: my-service-local
    resources: 11
    api keys:
      None
    endpoints:
      http://localhost:4566/restapis/0i514w1of2/local/_user_request_
    functions:
      hello: my-service-local-hello
    layers:
      None
    ```
2. Testing the endpoint - Once it's deployed on localstack, the URL to the endpoint is formed by concatenating the endpoint returned and the function name with a slash in between - which is not consistent with AWS's actual behaviour (as for right now). (reference issue [here](https://github.com/localstack/serverless-localstack/issues/28#issuecomment-500199803)); something like this:

    `curl -X POST http://localhost:4566/restapis/0i514w1of2/local/_user_request_/hello`

    In this example, a successful response should return:
    
    `{"message": "Hello lambda!"}`


## Deployment to AWS
At some point, you may want to deploy your app to AWS for real, to do so, follow the following steps:

1. Add your real aws credentials profile in the `~/.aws/credentials` file. You can find out more in step 4 of the [parent readme](../../README.md).
2. under the `provider` section in `serverless.yml`, edit the `profile` attribute to correspond to your real aws credentials

3. Deploy to AWS (note that without the `--stage local` option, it will now deploy to aws for real)

    `serverless deploy`

    If successful, the response should be similar to the one above, except this time containing the actual aws endpoint used to invoke the function.

## Converting this template to your own project
To turn this template into your own project, simply copy the `serverless.yml` file to your project, and edit the attributes to suit your needs - mainly the service name and function name(s). The .yml config file is labelled with comments for more clarity.
