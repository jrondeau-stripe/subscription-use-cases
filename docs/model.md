# Model your business

Products and Prices are the key API objects you model your business with. You pass the Price ID value to the calls to the Stripe API to create and maintain subscriptions.

In the samples, you create these objects only once, outside the flow of the rest of the application. We show you how to create them in the Dashboard or with the Stripe CLI, but you can also create them with calls to the Stripe API in any of the languages that Stripe supports.

Products represents the items your customer subscribes to. Prices represent how much and how often to charge for the product.

