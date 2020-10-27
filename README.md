# Memo-Aws

https://aws.amazon.com/fr/local/france/

## Doc générale

https://boto3.amazonaws.com/v1/documentation/api/latest/index.html

https://aws.amazon.com/fr/blogs/france/les-10-choses-a-savoir-pour-les-architectes-serverless/

https://docs.aws.amazon.com/cli/index.html

## Setup credentials

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-set-up-credentials.html

## Python Bonne pratique

```bash

# Créer un nouvel environnement virtuel
 python -m venv envirovirtuelaws
 
 # Activer cet environnement
Démarrer en Admin Powershell
set-executionpolicy remotesigned

.\envirovirtuelaws\Scripts\activate.ps1

PS C:\Code\WorkspaceVSCode> .\envirovirtuelaws\Scripts\activate.ps1
(envirovirtuelaws) PS C:\Code\WorkspaceVSCode>

# Pour une desactivation d'un environnement virtuel
deactivate

# Créer son repertoire projet (plutot initialiser avec VSCode)
Ex: sam init

# Installer les dependances

$ pip install requests pytest

Sous Windows :
$ pip freeze > requirements.txt

Sous Linux :
$ pip freeze | grep pytest >> requirements.txt
$ pip freeze | grep requests >> requirements.txt


#Toutes les dépendances du projet seront installées automatiquement par un autre utilisateur:

pip install -r requirements.txt

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


### Init

1. Commencer par mettre en place un environnement virtuel (ie. bonnes pratiques)

2. Initialisation de AWWS SAM par ligne de commande ou VSCode

Par VSCode : Ajout de pre-conf pour run avec VSCode

```bash
sam init
```

### Indus

Modifier hello_world/requirements.txt

```txt
requests
pytest
pytest-mock
```

`pip install -r hello_world/requirements.txt`

### Build

Build your application with the `sam build` command.

```bash
$ sam build
```

ou

If your functions depend on packages that have natively compiled dependencies, use this flag to build your function :

```bash
$ sam build --use-container
```

### Use the SAM CLI to build and test locally

Run functions locally and invoke them with the `sam local invoke` command.

```bash
$ sam local invoke HelloWorldFunction --event events/event.json
```

The SAM CLI can also emulate your application's API. Use the `sam local start-api` to run the API locally on port 3000.

```bash
$ sam local start-api
$ curl http://127.0.0.1:3000/hello
```

Vous pouvez spécifier un certain nombre de valeurs à remplacer dans la demande pour simuler ce que vous attendez d'une demande réelle

```bash
$ sam local generate-event apigateway aws-proxy --body "" --path "hello" --method GET > api-event.json
```

### Deploiement AWS

To build and deploy your application for the first time, run the following in your shell:

```bash
sam build --use-container
sam deploy --guided
```

### Le Debugging

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

### Fetch, tail, and filter Lambda function logs

To simplify troubleshooting, SAM CLI has a command called `sam logs`.

```bash
$ sam logs -n HelloWorldFunction --stack-name sam-app --tail
```

Voir : https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-logging.html

### Unit tests
Tests are defined in the `tests` folder in this project. Use PIP to install the [pytest](https://docs.pytest.org/en/latest/) and run unit tests.

```bash
$ pip install pytest pytest-mock --user
$ python -m pytest tests/ -v
```


### Cleanup

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
