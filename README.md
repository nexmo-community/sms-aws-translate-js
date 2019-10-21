# SMS Translation with AWS Translate

[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.svg)](https://nexmo.dev/aws-nexmo-sms-analysis-heroku)

This example uses AWS Translate to translate SMS messages into English.

SMS Messages sent through Nexmo will be sent to AWS Translate and the translations sent to the console.

## AWS Translate

Reference: [https://aws.amazon.com/translate/resources/](https://aws.amazon.com/translate/resources/)
API Docs: [https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/Translate.html](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/Translate.html)
GitHub: [https://github.com/aws/aws-sdk-js](https://github.com/aws/aws-sdk-js)

Create an [IAM user](https://console.aws.amazon.com/iam/home) with the `TranslateFullAccess` policy attached. Copy the IAM user `Access Key ID`, `Secret Access Key`, and the AWS region being used.


## Running the App

This sample app uses a `.env` file to provide the API key and URL.

Copy the provided `.env.example` file to a new file called `.env`:

```
cp .env.example > .env
```

Then update the values with those from the AWS Translate enabled IAM user, and then save.

```
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_REGION=
```

Also, expose the application to the internet using tools like [ngrok](https://ngrok.com/). To see how, [check out this guide](https://www.nexmo.com/blog/2017/07/04/local-development-nexmo-ngrok-tunnel-dr/).

### Using Docker

To run the app using Docker, run the following command in a terminal:

```
docker-compose up
```

This will create a new image with all the dependencies and run it at http://localhost:3000.

### Using Node

To run the app using node, run the following command in a terminal:

```
npm install && node index.js
```

This will install all the dependencies and run it at http://localhost:3000.

## Linking the app to Nexmo

For this example app a Nexmo number and SMS webhook setup is needed.

This can be achieved with the Nexmo CLI. Install the CLI by following [these instructions](https://github.com/Nexmo/nexmo-cli#installation).

### Rent a New Virtual Number

Renting a number will need to be in place. This can also be achieved using the CLI by running this command:

```
nexmo number:buy --country_code US
```

### Adding the SMS Webhook

Update the number created with the URL of the hosted or local server.

```
nexmo link:sms phone_number https://my-hostname/message
```

## Try it out

With the example Node application running in the terminal, send various foreign language SMS messages to the virtual number.  The terminal will output the response from AWS Translate.


## Extend
This app prints out to the console. For integration with an application, extend the `translateText` function to suit your needs.
