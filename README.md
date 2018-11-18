# gatsby-source-stripe

Source plugin for pulling in data from the [Stripe API](https://stripe.com/docs/api). Current with Stripe API version 2018-11-08.

This plugin is a source plugin, so it only brings in the data (to be used, for example, in creating a Stripe dashboard, or an e-commerce store). To actually edit the data in your Stripe account, to handle transactions, make charges, you will need to use some kind of backend server or serverless architecture.

Check out the [CHANGELOG](https://github.com/njosefbeck/gatsby-source-stripe/blob/master/CHANGELOG.md) for past and upcoming updates.

## Install

`npm install gatsby-source-stripe`

or

`yarn add gatsby-source-stripe`

## How to use

**NOTE: This plugin only supports Node v.10 and above, and has been tested against v10.13.0. If you experience any issues, first make sure you're running at least Node v.10.**

In the plugin options objects' array, specify the object types you would like to get data for. For example, if I'd like to get the lists of data for my balance transactions, customers, and subscriptions, my objects array would look like this: `['BalanceTransaction', 'Customer', 'Subscription']`.

Additionally, please only include your Stripe secret key via a [.env](https://www.npmjs.com/package/dotenv) file. We don't want your key ending up in your version-controlled source code!

Example below.

```javascript
// In your gatsby-config.js
plugins: [
  {
    resolve: `gatsby-source-stripe`,
    options: {
      objects: ['Balance', 'BalanceTransaction', 'Product', 'ApplicationFee', 'Sku', 'Subscription'],
      secretKey: 'stripe_secret_key_here'
    }
  }
]
```

### Supported List of Types

Below is a table with a list of the Stripe types supported in the options' objects array, as well as what Stripe API method the type maps to, and any other additional notes.

| Type | Stripe API Method | Notes |
| --- | --- | --- |
| Balance  | [stripe.balance.retrieve()](https://stripe.com/docs/api/balance/balance_retrieve?lang=node) | Not iterable |
| BalanceTransaction | [stripe.balance.listTransactions()](https://stripe.com/docs/api/balance/balance_history?lang=node) | None |
| Charge | [stripe.charges.list()](https://stripe.com/docs/api/charges/list?lang=node) | None |
| Customer | [stripe.customers.list()](https://stripe.com/docs/api/customers/list?lang=node) | None |
| Dispute | [stripe.disputes.list()](https://stripe.com/docs/api/disputes/list?lang=node) | None |
| Event | [stripe.events.list()](https://stripe.com/docs/api/events/list?lang=node) | None |
| File | [stripe.files.list()](https://stripe.com/docs/api/files/list?lang=node) | Not iterable |
| FileLink | [stripe.fileLinks.list()](https://stripe.com/docs/api/file_links/list?lang=node) | None |
| PaymentIntent | [stripe.paymentIntents.list()](https://stripe.com/docs/api/payment_intents/list?lang=node) | None |
| Payout | [stripe.payouts.list()](https://stripe.com/docs/api/payouts/list?lang=node) | None |
| Product | [stripe.products.list()](https://stripe.com/docs/api/products/list?lang=node) | None |
| Refund | [stripe.refunds.list()](https://stripe.com/docs/api/refunds/list?lang=node) | None |
| Coupon | [stripe.coupons.list()](https://stripe.com/docs/api/coupons/list?lang=node) | None |
| Invoice | [stripe.invoices.list()](https://stripe.com/docs/api/invoices/list?lang=node) | None |
| InvoiceItem | [stripe.invoiceItems.list()](https://stripe.com/docs/api/invoiceitems/list?lang=node) | None |
| Plan | [stripe.plans.list()](https://stripe.com/docs/api/plans/list?lang=node) | None |
| Subscription | [stripe.subscriptions.list()](https://stripe.com/docs/api/subscriptions/list?lang=node) | None |
| Account | [stripe.accounts.list()](https://stripe.com/docs/api/accounts/list?lang=node) | None |
| ApplicationFee | [stripe.applicationFees.list()](https://stripe.com/docs/api/application_fees/list?lang=node) | None |
| CountrySpec | [stripe.countrySpecs.list()](https://stripe.com/docs/api/country_specs/list?lang=node) | None |
| TopUp | [stripe.topUps.list()](https://stripe.com/docs/api/topups/list?lang=node) | None |
| Transfer | [stripe.transfers.list()](https://stripe.com/docs/api/transfers/list?lang=node) | None |
| IssuingAuthorization | [stripe.issuing.authorizations.list()](https://stripe.com/docs/api/issuing/authorizations/list?lang=node) | Issuing is in closed beta. Can only get data if you have access to the beta. |
| IssuingCardholder | [stripe.issuing.cardholders.list()](https://stripe.com/docs/api/issuing/cardholders/list?lang=node) | Issuing is in closed beta. Can only get data if you have access to the beta. |
| IssuingCard | [stripe.issuing.cards.list()](https://stripe.com/docs/api/issuing/cards/list?lang=node) | Issuing is in closed beta. Can only get data if you have access to the beta. |
| IssuingDispute | [stripe.issuing.disputes.list()](https://stripe.com/docs/api/issuing/disputes/list?lang=node) | Issuing is in closed beta. Can only get data if you have access to the beta. |
| IssuingTransaction | [stripe.issuing.transactions.list()](https://stripe.com/docs/api/issuing/transactions/list?lang=node) | Issuing is in closed beta. Can only get data if you have access to the beta. |
| TerminalLocation | [stripe.terminal.locations.list()](https://stripe.com/docs/api/terminal/locations/list?lang=node) | None |
| TerminalReader | [stripe.terminal.readers.list()](https://stripe.com/docs/api/terminal/readers/list?lang=node) | None |
| Order | [stripe.orders.list()](https://stripe.com/docs/api/orders/list?lang=node) | None |
| OrderReturn | [stripe.orderReturns.list()](https://stripe.com/docs/api/order_returns/list?lang=node) | None |
| Sku | [stripe.skus.list()](https://stripe.com/docs/api/skus/list?lang=node) | None |
| SigmaScheduledQueryRun | [stripe.sigma.ScheduledQueryRuns.list()](https://stripe.com/docs/api/sigma/scheduled_queries/list?lang=node) | Only works with live secret keys, not test keys |
| WebhookEndpoint | [stripe.webhookEndpoints.list()](https://stripe.com/docs/api/webhook_endpoints/list?lang=node) | None |


## Expanding Objects

Expanding all Stripe objects is tricky, as some objects have a lot of nested sub-objects to expand! We've tried to auto-expand as much of the top-level objects as possible. You can peruse a list of what is expanded per object in the `stripeObjects.json` file.

## Auto-pagination

**NOTE: Due to stripe-node's [autopagination recommendations](https://github.com/stripe/stripe-node#auto-pagination) this plugin only supports Node v.10 and above, and has been tested against v10.13.0. If you experience any issues, first make sure you're running at least Node v.10.**

All list responses are fully paginated.

## How to query

You can query all of the different Stripe object data like the following:

```graphql
{
  allStripeCustomer {
    edges {
      node {
        id,
        active,
        attributes,
        skus {
          id
        }
      }
    }
  }
}
```

Just replace "Customer" with any of the types used in your objects config array.

You can also query for a specific Stripe object like this:

```graphql
{
  stripeCustomer(id: { eq: "customer_id_here" }) {
    id,
    name
  }
}
```

When using GraphiQL, click on "Docs" in the top-right corner of the screen to explore all of the Stripe data being brought in, including their schemas. Additionally, check out Gatsby's handy [GraphQL Reference](https://www.gatsbyjs.org/docs/graphql-reference/) for information about filtering, sorting, etc.

## Develop

Would you like to help maintain this project? We would love your help! Checkout [issues](https://github.com/njosefbeck/gatsby-source-stripe/issues) and look for tags labeled `help wanted`. Also, feel free to get in touch via Twitter @njosefbeck.

To set up the project locally, follow these steps.

1) Make sure you're on at least Node v.10.
2) Fork the repo and pull it down locally. For ease of testing, we recommend pulling it into an existing Gatsby project, in a `plugins` directory.
3) Run `npm run build` in the console, to transpile the code for testing and running in your project.
4) Add the plugin, with options, to `gatsby-config.js`.
4) Hack away!
