# Memo-Aws

https://aws.amazon.com/fr/local/france/

## AWS Serverless Application Model

https://aws.amazon.com/fr/serverless/sam/

Build your application with the `sam build --use-container` command.

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

To simplify troubleshooting, SAM CLI has a command called `sam logs`.

```bash
$ sam logs -n HelloWorldFunction --stack-name MonApplicationAwsSAM --tail
```

[SAM CLI Doc logging](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-logging.html).



## Installation d'un poste de dev 

1. Installer Git

2. Installer Docker (prerequis : wsl2)

3. Installer python

Sur site officiel Ex: python-3.8.6-amd64.exe

4. Installer VSCode

5. Installer AWS toolkit pour VSCode

6. Installer Plugin Python pour VSCode

6. Installer AWS CLI

https://aws.amazon.com/fr/cli/

7. Installer AWS SAM CLI

https://aws.amazon.com/fr/serverless/sam/
