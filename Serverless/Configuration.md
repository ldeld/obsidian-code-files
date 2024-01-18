
### serverless.yml

Configures stuff like python version, includes plugins like [WSGI](Serverless/WSGI) (equivalent to Rack)
Example of a file (using a flask app):
```yml
service: serverless-flask

plugins:
  - serverless-python-requirements
  - serverless-wsgi

custom:
  wsgi:
    app: app.app
    packRequirements: false


provider:
  name: aws
  runtime: python3.11
  stage: dev
  region: eu-west-3

functions:
  app:
    handler: wsgi_handler.handler
    events:
      - http: ANY /
      - http: 'ANY /{proxy+}'

```

package.json file: adds some plugins (not sure why they use node instead of python, )

requirements.txt: Like a Gemfile