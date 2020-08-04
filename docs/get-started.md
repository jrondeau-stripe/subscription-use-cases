# Get started

Currently the samples for the different use cases are placed in separate directories, so be aware that when you clone the repo you're getting all of them. Make sure to work from the directory that contains the code for your use case. For details, see [how to model your subscription business](/model). TODO CHECK LINK SYNTAX BC I'VE FORGOTTEN EVERYTHING FROM THE TIME BEFORE PAYSERVER

Each sample includes server implementations in all the languages Stripe provides libraries for.

## Prerequisites

- A Stripe account
- Your API keys
- Price IDs

## Clone the repo and configure your environment

The Stripe CLI is the fastest way to clone and configure a sample to run locally. It also provides functionality for locally testing webhooks and your Stripe integration.

Prerequisite: A Stripe account and your API keys

### Clone and configure the sample with the CLI

Prerequisite: [CLI installed](https://github.com/stripe/stripe-cli#installation) and [paired with your Stripe account](https://stripe.com/docs/stripe-cli#login-account)

In your terminal shell, run the Stripe CLI command to clone the sample:

```
stripe samples create subscription-use-cases
```

The CLI will walk you through picking your integration type, server and client languages, and configuring your `.env` config file with your Stripe API keys.

### Clone and configure manually

If you do not want to use the Stripe CLI, you can manually clone and configure the sample:

```
git clone git@github.com:stripe-samples/subscription-use-cases.git
```

Copy the `.env.example` file into a file named `.env` in the folder of the server you want to use. For example:

```
cp .env.example server/node/.env
```
Add your API keys:

```
STRIPE_PUBLISHABLE_KEY=<replace-with-your-publishable-key>
STRIPE_SECRET_KEY=<replace-with-your-secret-key>
```

`STATIC_DIR` tells the server where the client files are located and does not need to be modified unless you move the server files.

**2. Create Products and Plans on Stripe**

This sample requires a [Price](https://stripe.com/docs/api/prices) ID to create the subscription. Products and Plans are objects on Stripe that you use to model a subscription.

You can create Products and Prices [in the Dashboard](https://dashboard.stripe.com/products) or with the [API](https://stripe.com/docs/api/prices/create). Create a Price to run this sample and add it to your `.env`.

**3. Follow the server instructions on how to run:**

Pick the server language you want and follow the instructions in the server folder README on how to run.

```
cd server/node # there's a README in this folder with instructions
npm install
npm start
```

**4. [Optional] Run a webhook locally:**

You can use the Stripe CLI to forward webhook events to your server running locally.

If you haven't already, [install the CLI](https://stripe.com/docs/stripe-cli) and [link your Stripe account](https://stripe.com/docs/stripe-cli#link-account).

```
stripe listen --forward-to localhost:4242/webhook
```

The CLI will print a webhook secret key to the console. Set `STRIPE_WEBHOOK_SECRET` to this value in your .env file.

You should see events logged in the console where the CLI is running.

When you are ready to create a live webhook endpoint, follow our guide in the docs on [configuring a webhook endpoint in the dashboard](https://stripe.com/docs/webhooks/setup#configure-webhook-settings).

## FAQ

Q: Why did you pick these frameworks?

A: We chose the most minimal framework to convey the key Stripe calls and concepts you need to understand. These demos are meant as an educational tool that helps you roadmap how to integrate Stripe within your own system independent of the framework.

Q: Can you show me how to build X?

A: We are always looking for new recipe ideas, please email dev-samples@stripe.com with your suggestion!

## Author(s)

- [@ctrudeau-stripe](https://twitter.com/trudeaucj)
- [@suz-stripe](https://twitter.com/noopkat)
