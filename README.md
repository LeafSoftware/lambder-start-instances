# lambder-start-instances

start-instances is an AWS Lambda function for use with Lambder.

## REQUIRES:
* python-lambder

This lambda function starts any EC2 instances that match the following:

* instance is stopped
* instance is tagged with Key: 'LambderStart'

It is usually paired with lambder-stop-instances and used to run instances only
during business hours to save money.

## Installation

1. Clone this repo
2. `cp example_lambder.json  lambder.json`
3. Edit lambder.json to set your S3  bucket
4. `lambder function deploy`

## Usage

Schedule the function with a new event. Rember that the cron expression is
based on UTC.

    lambder events add \
      --name StartInstances \
      --function-name Lambder-start-instances
      --cron 'cron(0 12 ? * MON-FRI *)' \

## TODO

* Parameterize the tag in the input event object
