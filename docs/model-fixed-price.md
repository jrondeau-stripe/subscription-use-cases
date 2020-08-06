# Model your fixed-price business

The sample assumes two Price IDs and two Products, one for each Price. Each product bills at monthly intervals, with prices of 5 USD for the basic service and 15 USD for the premium service. Here's how to create them [with the CLI](#with-the-stripe-cli) or [in the Dashboard](#in-the-dashboard):

TODO figure out best place to put explanation about hard-coded id values. or don't hard-code them, but here for the CLI it's nice to see the exact sample response id passed in the next example to the create price call.

## With the Stripe CLI

Create the product object for the premium service:

```
stripe products create \
  --name="Billing Guide: Premium Service" \
  --type=service \
  --description="Premium service with extra features"
```

The response object includes an id value that you'd store in your database in a complete production integration. For this sample, we store it in the [`.env` file](LINK):

```
{
  "id": "prod_H94k5odtwJXMtQ",
...
}
```

Pass this product ID to a call to create the price object:

```
stripe prices create \
  -d product=prod_H94k5odtwJXMtQ \
  -d unit_amount=1500 \
  -d currency=usd \
  -d "recurring[interval]"=month
```

Create the product and price objects for the basic product in the same way, and add the price ID to your `.env` file.

A response to the create prices call looks like:

```
{
  "id": "price_HGd7M3DV3IMXkC",
  "object": "price",
  "product": "prod_HGd6W1VUqqXGvr",
  "type": "recurring",
  "currency": "usd",
  "recurring": {
    "aggregate_usage": null,
    "interval": "month",
    "interval_count": 1,
    "trial_period_days": null,
    "usage_type": "licensed"
  },
  "active": true,
  "billing_scheme": "per_unit",
  "created": 1589319695,
  "livemode": false,
  "lookup_key": null,
  "metadata": {
  },
  "nickname": null,
  "unit_amount": 1500,
  "unit_amount_decimal": "1500",
  "tiers": null,
  "tiers_mode": null,
  "transform_quantity": null
}
```

## In the Dashboard