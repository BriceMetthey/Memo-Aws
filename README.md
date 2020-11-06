# Memo-Aws

https://aws.amazon.com/fr/local/france/

## Doc générale

https://boto3.amazonaws.com/v1/documentation/api/latest/index.html

https://aws.amazon.com/fr/blogs/france/les-10-choses-a-savoir-pour-les-architectes-serverless/

https://docs.aws.amazon.com/cli/index.html

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

## AWS Chalice

https://aws.github.io/chalice/index

https://aws.amazon.com/fr/blogs/developer/following-serverless-best-practices-with-aws-chalice-and-lambda-powertools/

https://aws.amazon.com/fr/blogs/developer/deploying-aws-chalice-application-using-aws-cloud-development-kit/


## AWS Lambda

https://docs.aws.amazon.com/lambda/latest/dg/lambda-python.html


## AWS Serverless Application Model

[Lien vers aws-sam.md](aws-sam.md)

## AWS Step Function

https://aws.amazon.com/fr/step-functions/

## Base de données RDS

Une doc pour aider à se connecter à une BDD RDS :

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAMDBAuth.Connecting.Python.html

Voici les  dépendances obligatoires :
```
pip install wheel 
pip install boto3
pip install mysql-connector-python
```

Créer un nouveau security group et autoriser mon adresse IP

Modifier la base : laisser le subnet + lier la base au nouveau security group  et enlever le security group alloué par defaut

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
