# Model your business

Products and Prices are the key API objects you model your business with. You pass the Price ID value to the calls to the Stripe API to create and maintain subscriptions.

In the samples, you create these objects only once, outside the flow of the rest of the application. We show you how to create them in the Dashboard or with the Stripe CLI, but you can also create them with calls to the Stripe API in any of the languages that Stripe supports.

Products represents the items your customer subscribes to. Prices represent how much and how often to charge for the product. The different business models represented by the samples show how you might add multiple prices for the same product, or specify only one price per product, depending on how you want to charge for the goods or services you offer.

See these pages for details about how to create Products and Prices for different business models:

- [Fixed-price subscriptions](model-fixed-price.md), where customers pay the same amount for each product or service you offer
- [Per-seat subscriptions](model-per-seat.md), where customers pay depending on how many units (seats) of a product or service they purchase
- [Metered billing](model-metered.md), where customers pay depending on how much they use of a service such as data storage, or messages sent
