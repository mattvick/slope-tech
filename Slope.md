# Slope tech research

## Overview of requirements

Several moving parts including:

1. [Marketing website](#marketing-website)
1. [Demo website](#demo-website)
1. [Developer documentation](#developer-documentation)
1. [Public API](#public-api)
1. [Snippet code](#snippet-code)
1. [Injection code](#injection-code)
1. [Payment popup](#payment-popup)
1. [Third parties payment providers](#third-parties-payment-providers)
1. [Buyer web app](#buyer-web-app)
1. [Seller web app](#seller-web-app)
1. [Support](#support)

**Jump to:**

- [Questions](#questions)
- [Conclusions](#conclusions)

## How the payment flow works

https://developers.slope.so/docs/payment-flow

The Slope customer business integrates the following on their checkout page:

- Create an order - programmatically pass order information to the [Slope public API](#public-api)
- Generate an order intent token on their servers
- Add a [JavaScript code snippet](#snippet-code)

There's a bit of work involved. Most probably requiring a software engineer, rather than a business owner.

## Marketing website

https://slopepay.com/

You've seen it. It outlines the Slope business proposition.

## Demo website

https://demo.slope.so/

A mockup of a seller business website used to demo the Slope payment flow.

## Developer documentation

https://developers.slope.so/docs

Pages of instrustions outlining how to integrate and work with Slope.

## Public API

http://api.slope.so/v3/

The selling business uses this to programmatically communicate with Slope

## Snippet code

The selling business uses this to:

- Add a "Pay with Slope" button
- Embed and open the [Slope payment popup](#payment-popup)

```js
<script src="https://checkout.slope.so/slope.js?pk={{PUBLIC_KEY}}"></script>
<script type="text/javascript">
    window.initializeSlope({
        intentSecret: ORDER_INTENT_SECRET,
    })
</script>
<button onclick="window.Slope.open()">Pay with Slope</button>
```

## Injection code

https://checkout.slope.so/slope.js

This code:

- Injects the payment popup into the selling business' checkout
- Opens the payment popup when the "Pay with Slope" button is clicked

## Payment popup

https://checkout.sandbox.slope.so/v2/initial

A fullscreen overlay with multiple steps to complete the payment.

- Authentication (Customer login)
- Integration with [third parties payment providers](#third-parties-payment-providers)

Contains forms for data entry - FYI _forms kinda suck_ - they are tedious and time-consuming due to:

- Validation
- Error states
- Multi step state management

## Third parties payment providers

Used to add:

- Bank account [Plaid](https://plaid.com/)
- Credit card [Stripe](https://stripe.com/)
- Debit card - no option, I'm guessing because this terminolgy/technology isn't used much in the US

**Benefits of using third patries payment providers, vs self-hosting:**

1. Faster setup
1. Removal of barriers to entry
1. Lower level of [PCI Compliance](https://www.pcicomplianceguide.org/faq/#1) required - [Payment Card Industry Data Security Standard (PCI DSS)](https://en.wikipedia.org/wiki/Payment_Card_Industry_Data_Security_Standard)

## Buyer web app

https://pay.slope.so/login?type=email

We'll need to book a demo to view this. I imagine it is a place where buyer businesses can view and manage their payments.

Probably contains:

- A dashboard - with an overview of payments
- Individual payment view with calls to action

## Seller web app

Not sure if this exists. Seller businesses may only be able to interact with Slope via the [Public API](#public-api)

## Customer support

- support@slope.so
- 1-202-977-3324

They probably use some third party customer services software like [Zendesk](https://www.zendesk.com/) to manage customer support enquiries.

I didn't see any chat on their [marketing website](#marketing-website), but they may have this in their [buyer web app](#buyer-web-app).

## Questions

- What percentage of B2B businesses have an online checkout?
- What percentage of B2B businesses' customers prefer to pay via an online checkout?
- Could we initally target offline businesses
   - Would there be any benefit in doing that?

## Conclusions

- Nothing is beyond my knowledge and experience or anything that I couldn't figure out
- There are many moving parts
- Would be too time-consuming for a single engineer to build all these parts
- Likely best approach would be to raise investment and then build a team of engineers
