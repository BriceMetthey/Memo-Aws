# AWS Serverless Application Model

https://aws.amazon.com/fr/serverless/sam/

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html

https://aws.amazon.com/fr/serverless/serverlessrepo/


## Init

1. Commencer par mettre en place un environnement virtuel

2. Initialisation de AWS SAM par ligne de commande ou VSCode

Par VSCode : Ajout de pre-conf pour run avec VSCode

```bash
sam init
```

## Indus

A chaque ajout de dependances penser à fixer le fichier requirements.txt (Tips : Attention à l'encodage)

`pip freeze > requirements.txt`

`pip install -r xxx/requirements.txt`

## Build

Build your application with the `sam build` command.

`sam build`

If your functions depend on packages that have natively compiled dependencies, use this flag to build your function :

`sam build --use-container`

## Use the SAM CLI to build and test locally

Run functions locally and invoke them with the `sam local invoke` command.

`sam local invoke HelloWorldFunction --event events/event.json`

The SAM CLI can also emulate your application's API. Use the `sam local start-api` to run the API locally on port 3000.

```bash
$ sam local start-api
$ curl http://127.0.0.1:3000/hello
```

Vous pouvez spécifier un certain nombre de valeurs à remplacer dans la demande pour simuler ce que vous attendez d'une demande réelle

```bash
$ sam local generate-event apigateway aws-proxy --body "" --path "hello" --method GET > api-event.json
```

## Deploiement AWS

To build and deploy your application for the first time, run the following in your shell:

```bash
sam build --use-container
sam deploy --guided
```

## Le Debugging avec VSCode

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-test-and-debug.html

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-using-debugging-python.html

Suivre la doc AWS officielle précedente avec quelques nuances ...

workspace.json de Visual studio => corriger le path de localRoot

```json
{
	"name": "SAM CLI DEBUG MODE",
	"type": "python",
	"request": "attach",
	"port": 5890,
	"host": "localhost",
	"pathMappings": [
		{
			"localRoot": "${workspaceFolder}/sam-app/hello_world/build",
			"remoteRoot": "/var/task"
		}
	]
}
```

template.yaml de l'application SAM => Corriger CodeUri

```yaml
Resources:
  HelloWorldFunction:
    Type: AWS::Serverless::Function # More info about Function Resource: https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md#awsserverlessfunction
    Properties:
      CodeUri: hello_world/build/
      Handler: app.lambda_handler
      Runtime: python3.8
      Events:
        HelloWorld:
          Type: Api # More info about API Event Source: https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md#api
          Properties:
            Path: /hello
            Method: get
```

## Fetch, tail, and filter Lambda function logs

To simplify troubleshooting, SAM CLI has a command called `sam logs`.

```bash
sam logs -n HelloWorldFunction --stack-name sam-app --tail
```

Voir : https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-logging.html

## Unit tests
Tests are defined in the `tests` folder in this project. Use PIP to install the [pytest](https://docs.pytest.org/en/latest/) and run unit tests.

```bash
$ pip install pytest pytest-mock --user
$ python -m pytest tests/ -v
```


## Cleanup

To delete the sample application, use the AWS CLI.

```bash
aws cloudformation delete-stack --stack-name MonApplicationAwsSAM
```

Ou bien : https://console.aws.amazon.com/cloudformation.

In the left navigation pane, choose Stacks.

In the list of stacks, choose the stack you created.


## SAM & KMS

KMS use case : 

- https://dzone.com/articles/aws-kms-use-case-with-serverless-application-model

