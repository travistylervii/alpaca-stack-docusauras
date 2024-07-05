---
sidebar_position: 6
---

# Setup Stripe

To accept payments online, we need a merchant account. While there are several options like PayPal or Authorize.net, Stripe is the most popular due to its polished developer integration and comprehensive documentation. This tutorial will guide you through setting up Stripe and integrating it into your application.

## Video Tutorial
In this video I go over the details on how to setup stripe integration and products to the Alpaca Stack boilerplate template.

### Setup Stripe Integration
<div className="video-responsive">
<iframe width="100%" height="100%" src="https://www.youtube.com/embed/n28QqUwMZWk?si=Du2xgkuZT4wAOkpX" title="YouTube video player" frameBorder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerPolicy="strict-origin-when-cross-origin" allowFullScreen></iframe>
</div>

## Written Tutorial

### Setup Stripe Ingegration

#### About Stripe
Stripe is an online payment processing platform that allows businesses to accept payments over the internet. It provides a suite of payment APIs that support various payment methods, including credit cards, bank transfers, and digital wallets.

Stripe is widely used for its robust security features, extensive documentation, easy integration with various programming languages, and support for global transactions. This makes it a convenient and reliable choice for businesses of all sizes looking to handle online payments efficiently.

Learn more at: [stripe.com](http://stripe.com)

### 1. Setup Stripe API Keys

1. If you don’t already have a Stripe account, go to [stripe.com](http://stripe.com) and register for an account.
2. Once registered, head over to your Stripe settings ([Stripe Account Settings](https://dashboard.stripe.com/settings/account)) and click on the business link to complete your business details. Ensure all relevant sections under settings are filled out to ensure you get paid correctly.

### 2. Add Environment Variables

1. In Stripe, click the "Developers" link in the top right, then select "API keys".
2. Enable "test mode" by toggling the switch in the top right next to the developers link. 
3. Copy the test keys and paste them into your `.env` file: 
   - `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=your_publishable key`
   - `STRIPE_SECRET_KEY=your_secret_key`

Ensure that in production, you use the live API keys.
Ignore the webhook key for now; we will address it later when setting up the production environment.

### Setup The Checkout Page
### 1. Setup Stripe Plans / Products

With the Stripe environment variables set in your `.env` file, you can now add your products:

1. Go to the product catalog in the Stripe dashboard ([Stripe Product Catalog](https://dashboard.stripe.com/test/products?active=true)).
2. Add a new product by filling out the required fields.
3. After adding the product, go back into the product details and copy the API ID for the plan/product.
4. Update the `site.config.js` file in your app by replacing the current plan data with your own. Replace the `priceID` keys with the API ID for both development and production environments.
5. Fill out any additional information required for your plan.

### 2. Test Checkout Page

1. In the app source code, there is an API route under `/app/api/stripe/create-checkout`. This function generates the dynamic checkout page for Stripe.
   - It first checks if the current user has a customer ID in the database. If not, it creates one in Stripe and saves it to the user record in the database, then it creates a checkout form and displays it on the screen.
   - This API route can be used anywhere on your site to create a checkout form.
2. There is a client component called `BuyNowBtn.ts` located at `/components/buy-now-btn.ts` that uses this API route. Place this button anywhere on your site to create a Stripe checkout form. It is currently used in the pricing boxes.
3. Go to the homepage of your site, scroll down to the pricing section (`http://localhost:3000/#pricing-section`), and click "Buy Now" to test your checkout page.
4. If the checkout page does not show, check your console logs for error information.
5. If the checkout page displays correctly, test the form with a test card:
   - Card #: `4242 4242 4242 4242`
   - Expiration: Any future date (e.g., `05/55`)
   - CVC: Any three digits (e.g., `555`)

6. After paying, you should be redirected to a thank you page. The redirect page URL can be changed in the site-config.ts for each plan.

By following these steps, you should have Stripe fully integrated and functional in your application, allowing you to accept payments seamlessly.

### Setup Stripe Webhooks
### Setup Webhooks for Local Development
1. On the stripe dashboard navigate to the "Webhooks" section under "Developers".
2. Click on "Add endpoint" and use the following for local development:
  - URL: `http://localhost:3000/api/webhook/stripe`
3. Install the Stripe CLI tool and use the following command to forward events to your local environment:
```bash
stripe listen --forward-to localhost:3000/api/webhook/stripe
```
4. Copy the webhook signing secret and store it in your environment variables:
  - `STRIPE_WEBHOOK_SECRET=your_webhook_secret`

5. Make sure the stripe listen command is running everytime you make a test purchase on your local. If you add a console.log in the `api/webbook/stripe/route.ts` file and make a test purchase, you will see the webhook working. 

Here you can test each webhook event and ensure the correct code is executed for each event as well as add your own custom code like sending a personalized email when your product is purchased. 

### Setup Webhooks for Production
1. In the stripe dashboard navigate to the "Webhooks" section, add a new endpoint with your production URL:
  - URL: https://your-domain.com/api/webhook/stripe
2. Select the events you want to listen for. Alpaca Stack Default events are:
  - checkout.session.completed
  - checkout.session.expired
  - customer.subscription.deleted
  - customer.subscription.updated
  - invoice.paid
  - invoice.payment_failed

3. Save the endpoint and copy the webhook signing secret to your production environment variables.
4. Deploy your app, and test purchase. 

