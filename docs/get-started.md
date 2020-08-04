# Get started

Currently the samples for the different use cases are placed in separate directories, so be aware that when you clone the repo you're getting all of them. Make sure to work from the directory that contains the code for your use case.

Each sample includes server implementations in all the languages Stripe provides libraries for.

## Prerequisites

TODO add links

- A Stripe account
- Your API keys
- The Stripe client library for the language you want to work in 
- The Stripe CLI (optional but recommended)

## Clone the repository and configure your environment with the CLI

The Stripe CLI is the fastest way to clone and configure a sample to run locally. It also provides functionality for locally testing webhooks and the rest of your Stripe integration.

In your terminal shell, run the Stripe CLI command to clone the sample:

```
stripe samples create subscription-use-cases
```

You're asked to choose your integration type and server and client languages, and provide your Stripe API keys to include in your `.env` config file.

## Clone and configure manually

Or you can manually clone and configure the sample:

```
git clone git@github.com:stripe-samples/subscription-use-cases.git
```

Copy `.env.example` to a file named `.env` in the folder of the server you want to use. For example:

```
cp .env.example <use_case_directory>/server/node/.env
```
Add your API keys:

```
STRIPE_PUBLISHABLE_KEY=<replace-with-your-publishable-key>
STRIPE_SECRET_KEY=<replace-with-your-secret-key>
```

`STATIC_DIR` tells the server where the client files are located and does not need to be modified unless you move the server files.

## Model your business with Products and Prices

You also need to add Price IDs to your `.env` file. Prices are a core object of the Stripe API, but you typically create them only when your business needs them. TODO figure out better way to explain simply why you'd put them in a .env file instead of calling Stripe from your server.  

Prices represent your business model, together with their parent object Products. To create the appropriate Price IDs, see [how to model your business](model.md).

## Run the server

Pick the server language you want and follow the instructions in the server folder README on how to run.

```
cd <use_case_directory>/server/node # there's a README in this folder with instructions
npm install
npm start
```

## [Optional] Set up a local webhook endpoint

You can use the Stripe CLI to forward webhook events to your local server.

```
stripe listen --forward-to localhost:4242/webhook
```

The CLI prints a webhook secret key to the console. Set `STRIPE_WEBHOOK_SECRET` to this value in your `.env` file.

You should see events logged in the console where the CLI is running.

When you are ready to create a live webhook endpoint, follow our guide in the docs on [configuring a webhook endpoint in the dashboard](https://stripe.com/docs/webhooks/setup#configure-webhook-settings).

## FAQ

Q: Why did you pick these frameworks?

A: We chose minimal frameworks to show only the key Stripe calls and concepts you need to understand. You need to do more work to build a complete integration with your app's chosen framework, but the samples should provide models for integration regardless of framework.

Q: Can you show me how to build X?

A: We are always looking for new ideas for Stripe samples. Feel free to email dev-samples@stripe.com with your suggestion!

## Author(s)

- [@ctrudeau-stripe](https://twitter.com/trudeaucj)
- [@suz-stripe](https://twitter.com/noopkat)
