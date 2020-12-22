# Memo-Aws

https://aws.amazon.com/fr/local/france/

## Doc générale

Le getting-started officiel :

- https://aws.amazon.com/fr/getting-started/

Approfondissement Serverless

- https://aws.amazon.com/fr/getting-started/deep-dive-serverless/

Outils pour développeurs sur AWS :

- https://aws.amazon.com/fr/products/developer-tools/

Boto3 documentation :

- https://boto3.amazonaws.com/v1/documentation/api/latest/index.html

Les 10 choses à savoir pour les architectes Serverless :

- https://aws.amazon.com/fr/blogs/france/les-10-choses-a-savoir-pour-les-architectes-serverless/

Documentation de l'interface de la ligne de commande AWS :

- https://docs.aws.amazon.com/cli/index.html

Comparaison des différentes approches techniques :

- https://www.thedevcoach.co.uk/serverless-approaches-comparison/

Le service CloudShell :

- https://aws.amazon.com/fr/cloudshell/

Le service de chaos engineering :

- https://aws.amazon.com/fr/fis/

Les services de Télémétrie :

- https://aws.amazon.com/fr/prometheus/

- https://aws.amazon.com/fr/grafana/


## Setup credentials

https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started-set-up-credentials.html

## Python Bonnes pratiques

```bash
# Créer un nouvel environnement virtuel
python -m venv envirovirtuelaws
 
# Activer un environnement virtuel
A faire une fois : Démarrer en Admin Powershell
set-executionpolicy remotesigned

.\envirovirtuelaws\Scripts\activate.ps1

# Pour une desactivation d'un environnement virtuel
deactivate

# Installer les dependances
pip install requests pytest

# Installer obligatoirement
pip install wheel 

# Freeze des dépendances dans le fichier requirements :
pip freeze > requirements.txt

# Installations auto par un autre utilisateur:
pip install -r requirements.txt

```

## AWS CloudFormation

https://docs.aws.amazon.com/cloudformation/index.html

## AWS CDK

https://docs.aws.amazon.com/cdk/latest/guide/home.html

https://cdkworkshop.com/

## AWS Chalice

Doc officielle :

- https://aws.github.io/chalice/index

- https://chalice.readthedocs.io/en/stable/

Passer du modèle Chalice au modèle SAM :

- https://aws.amazon.com/fr/blogs/developer/aws-chalice-now-supports-yaml-templates/

Utiliser Chalice avec Terraform :

- https://aws.github.io/chalice/topics/tf.html


## Terraform

Tuto Terraform et AWS :

- https://learn.hashicorp.com/collections/terraform/aws-get-started

Tuto Deployer une appli AWS Lambda avec Terraform :

- https://learn.hashicorp.com/tutorials/terraform/lambda-api-gateway

Bonnes pratiques de déploiement

- https://medium.com/galvanize/aws-lambda-deployment-with-terraform-24d36cc86533

## AWS Lambda

https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html

Blog sur des bonnes pratiques aws-lambda :

- https://aws.amazon.com/fr/blogs/architecture/best-practices-for-developing-on-aws-lambda/


Doc officielle sur les bonnes pratiques aws-lambda :

- https://docs.aws.amazon.com/fr_fr/lambda/latest/dg/best-practices.html


Utilisation des variables d'environnement AWS Lambda :

- https://docs.aws.amazon.com/fr_fr/lambda/latest/dg/configuration-envvars.html

Traitement parallèle en Python

- https://aws.amazon.com/fr/blogs/compute/parallel-processing-in-python-with-aws-lambda/

Testing and Deployment Best Practices for AWS Lambda

- https://youtu.be/zJQDAsWm-5k

## AWS et Front End

https://aws.amazon.com/fr/amplify/


## Modèle d'application sans serveur

https://aws.amazon.com/fr/serverless/


## AWS Serverless Application Model Framework

[Lien vers aws-sam.md](aws-sam.md)


## AWS Step Function

https://aws.amazon.com/fr/step-functions/

## API Gateway

https://aws.amazon.com/fr/api-gateway/

## Base de données RDS

Une doc pour aider à se connecter à une BDD RDS :

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.Connecting.Python.html

Voici les  dépendances obligatoires :

```bash
pip install wheel 
pip install boto3
pip install mysql-connector-python
# Pour fixer une erreur d'import pylint (mais l'exclure impérativement de requirements.txt):
pip install mysql-connector-python-rf
```

1. Rendre accessible publiquement la base

2. Créer un nouveau security group et autoriser mon adresse IP en entrant

3. Modifier la base : laisser le subnet + lier la base au nouveau security group  et enlever le security group alloué par defaut

4. Le code n'est pas forcément adapté pour fonctionner avec AWS SAM

```python
# Au lieu de ça :
boto3.Session(profile_name='RDSCreds')
# On fera :
boto3.Session(aws_access_key_id="xx", aws_secret_access_key="xx")
```

5. Pour autoriser un utilisateur ou un rôle IAM à se connecter à votre instance de base de données , vous devez créer une stratégie IAM. Après cela, vous attachez la stratégie à un utilisateur ou à un rôle IAM.

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.IAMPolicy.html

6. Avoir un utilisateur specifique avec les droits d'authentification IAM

Se connecter avec MySQLWorkbench à la base

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.DBAccounts.html

```sql
CREATE USER jane_doe IDENTIFIED WITH AWSAuthenticationPlugin AS 'RDS';
```

Bien utiliser le user maintenant pour se connecter à la base.

## Installation d'un poste de dev 

1. Installer Git

2. Installer Docker

3. Installer python

4. Installer VSCode

5. Installer AWS toolkit pour VSCode

6. Installer Plugin Python pour VSCode

7. Mettre en place un environment virtuel

8. Dans VSCode -> Command Palette -> Python : Select Interpreter -> Choisir le python.exe de votre enviro virtuel

9. Installer AWS CLI    https://aws.amazon.com/fr/cli/

10. Installer AWS SAM CLI   https://aws.amazon.com/fr/serverless/sam/
