# dynamodb-aws-cli

## Extension of official aws dynamodb-local image adding **aws cli** and **init scripts at container start-up**


This image extends the official [dynamodb-local docker image](https://hub.docker.com/r/amazon/dynamodb-local/) adding the `possibility to run custom scripts at start-up` (e.g. Run a script to create dynamodb table). and 
`includes the last version of aws cli`.

## Usage

### Run
> docker run -p 8000:8000 killboard/dynamodb-aws-cli

### Run with scripts at startup
Example script to create an table at start-up
```shellscript
#!/bin/bash

aws dynamodb create-table --region=us-east-1 --cli-input-json file://create-table-platform-transactions.json --endpoint-url http://localhost:8000
```

> docker run -v $(pwd)/example:/init-scripts -p 8000:8000 killboard/dynamodb-aws-cli