## Introduction
This repo serves as a simplistic template repo dedicated to developers anyone who wants to use [serverless](https://www.serverless.com/) with [localstack](https://github.com/localstack/localstack) integration in their aws projects. localstack is a very useful tool that simulates AWS stacks locally for the purpose of development and testing.

## Why this repo?
There overwhelming amounts of articles and documentation out there for each of the dependencies that can be difficult to follow and put together. The templates provided here are designed to be very concise with minimal configurations for developers who just want a starting point for their new projects.

## Prerequisites
There are a few essential tools that are required before you begin
- [Docker](https://www.docker.com/)
- [python](https://www.python.org/) (python3 recommended)
- [pip](https://pypi.org/project/pip/)
- [npm](https://www.npmjs.com/)

## Dependencies
1. Install the **serverless** framework used to interact and deploy to AWS

    `npm i -g serverless`

2. Install the **serverless-localstack** plugin (using serverless or npm)

    `serverless plugin install --name serverless-localstack` 

3. Install **localstack** (I recommend installing via a python [virtual environment](https://docs.python.org/3/tutorial/venv.html), but it's optional)

    `pip3 install localstack`

4. Setup dummy AWS credentials - Add a dummy profile to your aws credentials file    
    Edit the credentials file in the .aws folder and append the following lines:

    ```
    [localdummy]
    aws_access_key_id = dummy_id
    aws_secret_access_key = dummy_key
    ```
    or just

    `mkdir -p ~/.aws && echo "[localdummy]\naws_access_key_id = dummy_id\naws_secret_access_key = dummy_key" >> ~/.aws/credentials`
    
    if you on Mac of Linux. If you're unfamiliar with AWS credentials, you can find out more [here](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/setup-credentials.html).

5. Check out the templates folder for specific setups and continue the setup by following its `README.md` file.


## Contributing
Got another idea for a template that you think will be useful? Drop a PR and I'll be glad to add it in!

## Questions
Feel free to open an issues and inquiry about any part of repo, I'll do my best to address any questions and problems.
