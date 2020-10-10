# Memo-Aws

https://aws.amazon.com/fr/local/france/

## Doc générale

https://aws.amazon.com/fr/blogs/france/les-10-choses-a-savoir-pour-les-architectes-serverless/

https://docs.aws.amazon.com/cli/index.html


## Python Bonne pratique

```bash
sam init --runtime python3.6 --name python-debugging
cd python-debugging/

# Install dependencies of our boilerplate app
pip install -r hello_world/requirements.txt -t hello_world/build/

# Install ptvsd library for step through debugging
pip install ptvsd -t hello_world/build/

cp hello_world/app.py hello_world/build/
```

## AWS Chalice

https://aws.github.io/chalice/index

https://aws.amazon.com/fr/blogs/developer/following-serverless-best-practices-with-aws-chalice-and-lambda-powertools/

https://aws.amazon.com/fr/blogs/developer/deploying-aws-chalice-application-using-aws-cloud-development-kit/


## AWS Lambda

https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html


## AWS Serverless Application Model

https://aws.amazon.com/fr/serverless/sam/

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html

https://aws.amazon.com/fr/serverless/serverlessrepo/


```bash
sam init
```

--> Ensuite mettre en place un environnement virtuel !


Build your application with the `sam build --use-container` command.

```bash
$ sam build
```

ou

```bash
$ sam build --use-container
```

Run functions locally and invoke them with the `sam local invoke` command.

```bash
$ sam local invoke HelloWorldFunction --event events/event.json
```

The SAM CLI can also emulate your application's API. Use the `sam local start-api` to run the API locally on port 3000.

```bash
$ sam local start-api
$ curl http://localhost:3000/
```

Vous pouvez spécifier un certain nombre de valeurs à remplacer dans la demande pour simuler ce que vous attendez d'une demande réelle

```bash
$ sam local generate-event apigateway aws-proxy --body "" --path "hello" --method GET > api-event.json
```

Le Debugging

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-test-and-debug.html

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-using-debugging-python.html



To simplify troubleshooting, SAM CLI has a command called `sam logs`.

```bash
$ sam logs -n HelloWorldFunction --stack-name MonApplicationAwsSAM --tail
```

Voir : https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-logging.html


Tests are defined in the `tests` folder in this project. Use PIP to install the [pytest](https://docs.pytest.org/en/latest/) and run unit tests.

```bash
$ pip install pytest pytest-mock --user
$ python -m pytest tests/ -v
```

To build and deploy your application for the first time, run the following in your shell:

```bash
sam build --use-container
sam deploy --guided
```


To delete the sample application, use the AWS CLI.

```bash
aws cloudformation delete-stack --stack-name MonApplicationAwsSAM
```

Ou bien : https://console.aws.amazon.com/cloudformation.

In the left navigation pane, choose Stacks.

In the list of stacks, choose the stack you created.


## AWS Step Function

https://aws.amazon.com/fr/step-functions/


## Installation d'un poste de dev 

1. Installer Git

2. Installer Docker

3. Installer python

Sur site officiel

4. Installer VSCode

5. Installer AWS toolkit pour VSCode

6. Installer Plugin Python pour VSCode

Note : pylint (linter pour python) va demander à être installé à l'ouverture d'un fichier python.

6. Installer AWS CLI

https://aws.amazon.com/fr/cli/

7. Installer AWS SAM CLI

https://aws.amazon.com/fr/serverless/sam/
