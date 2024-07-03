---
sidebar_position: 6
---

# Setup Stripe

To accept payments online, we need a merchant account. While there are several options like PayPal or Authorize.net, Stripe is the most popular due to its polished developer integration and comprehensive documentation. This tutorial will guide you through setting up Stripe and integrating it into your application.

# Video Tutorial
In this video I go over the details on how to setup stripe integration and products to the Alpaca Stack boilerplate template.
<div className="video-responsive">
<iframe width="100%" height="100%" src="https://www.youtube.com/embed/n28QqUwMZWk?si=Du2xgkuZT4wAOkpX" title="YouTube video player" frameBorder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerPolicy="strict-origin-when-cross-origin" allowFullScreen></iframe>
</div>

# Written Tutorial

### About Stripe
Stripe is an online payment processing platform that allows businesses to accept payments over the internet. It provides a suite of payment APIs that support various payment methods, including credit cards, bank transfers, and digital wallets.

Stripe is widely used for its robust security features, extensive documentation, easy integration with various programming languages, and support for global transactions. This makes it a convenient and reliable choice for businesses of all sizes looking to handle online payments efficiently.

Learn more at: [stripe.com](http://stripe.com)

## Setup The Checkout Page

## 1 - Setup Stripe Test Account / Plans

1. If you don’t already have a Stripe account, go to [stripe.com](http://stripe.com) and register for an account.
2. Once registered, head over to your Stripe settings ([Stripe Account Settings](https://dashboard.stripe.com/settings/account)) and click on the business link to complete your business details. Ensure all relevant sections under settings are filled out to ensure you get paid correctly.

## 2 - Add Environment Variables

1. In Stripe, click the "Developers" link in the top right, then select "API keys".
2. Enable "test mode" by toggling the switch in the top right next to the developers link. 
3. Copy the test keys and paste them into your `.env` file:
   - `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY` for the "Publishable key".
   - `STRIPE_SECRET_KEY` for the "Secret Key".
4. Ignore the webhook key for now; we will address it later when setting up the production environment.

## 3 - Setup Stripe Plans / Products

With the Stripe environment variables set in your `.env` file, you can now add your products:

1. Go to the product catalog in the Stripe dashboard ([Stripe Product Catalog](https://dashboard.stripe.com/test/products?active=true)).
2. Add a new product by filling out the required fields.
3. After adding the product, go back into the product details and copy the API ID for the plan/product.
4. Update the `site.config.js` file in your app by replacing the current plan data with your own. Replace the `priceID` keys with the API ID for both development and production environments.
5. Fill out any additional information required for your plan.

## 4 - Test Checkout Page

1. In the app source code, there is an API route under `/app/api/stripe/create-checkout`. This function generates the dynamic checkout page for Stripe.
   - It first checks if the current user has a customer ID in the database. If not, it creates one in Stripe and saves it to the user record in the database, then it creates a checkout form and displays it on the screen.
   - This API route can be used anywhere on your site to create a checkout form.
2. There is a client component called `BuyNowBtn.ts` located at `/components/buy-now-btn.ts` that uses this API route. Place this button anywhere on your site to create a Stripe checkout form. It is currently used in the pricing boxes.
3. Go to the homepage of your site, scroll down to the pricing section (`localhost:3000/#pricing-section`), and click "Buy Now" to test your checkout page.
4. If the checkout page does not show, check your console logs for error information.
5. If the checkout page displays correctly, test the form with a test card:
   - Card #: `4242 4242 4242 4242`
   - Expiration: Any future date (e.g., `05/55`)
   - CVC: Any three digits (e.g., `555`)

6. After paying, you should be redirected to a thank you page. The redirect page URL can be changed in the `BuyNowBtn.ts` component.

By following these steps, you should have Stripe fully integrated and functional in your application, allowing you to accept payments seamlessly.

## Setup Stripe Webhook
Under construction, refer to video tutorial for now. 
