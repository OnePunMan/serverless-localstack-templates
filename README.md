# Introduction
This repo functions as a simple template dedicated to developers who want to use [serverless](https://www.serverless.com/) with [localstack](https://github.com/localstack/localstack). Localstack is a very useful tool that simulates AWS stacks locally for the purpose of development and testing.

## Why this repo?
There are an overwhelming amount of articles and documentation for each of the dependencies that can be difficult to follow and put together. These templates are designed to be very concise with minimal configurations - ideal for those who just want a quick starting point for their new projects.

## Prerequisites
There are a few essential tools that are required before you begin
- [Docker](https://www.docker.com/) (make sure it's running)
- [python](https://www.python.org/) (python 3 recommended)
- [pip](https://pypi.org/project/pip/) (usually already included when installing python)
- [npm](https://www.npmjs.com/)

## Dependencies
1. Install the **serverless** framework (run with `sudo` if you encounter permission errors)

    `npm i -g serverless`

2. Install **localstack** (I recommend installing via a python [virtual environment](https://docs.python.org/3/tutorial/venv.html), but it's optional)

    `pip3 install localstack`

3. Setup dummy AWS credentials - Add a *dummy* profile to your aws credentials file
    Either manually edit the `credentials` file in the `.aws` folder and append the following lines:

    ```
    [localdummy]
    aws_access_key_id = dummy_id
    aws_secret_access_key = dummy_key
    ```
    OR if you are on Mac or Linux, simply:

    `mkdir -p ~/.aws && echo "[localdummy]\naws_access_key_id = dummy_id\naws_secret_access_key = dummy_key" >> ~/.aws/credentials`

    You can also use your real credentials if you plan to deploy to AWS. Although localstack does not require real credentials, they must exist, that's why we're creating a dummy profile as a placeholder. If you're unfamiliar with AWS credentials, you can find out more [here](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/setup-credentials.html).

4. Create a serverless project from one of the [templates](templates) (or [from scratch](https://www.serverless.com/framework/docs/providers/aws/cli-reference/create/)). Each template has its own `README.md` file with more specific instructions.

5. Install the **serverless-localstack** plugin in your *serverless project directory*. The serverless-localstack plugin is *per-project* based, so it will only work in a serverless project folder (i.e. any folder with a `serverless.yml` file).

    `serverless plugin install --name serverless-localstack`


### Contributing
Got another idea for a template that you think will be useful? Drop a PR and I'll be glad to add it in!

### Questions
Feel free to open an issue regarding any questions or problems, I will do my best to address any problems.
