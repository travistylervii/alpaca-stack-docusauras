---
sidebar_position: 1
---

# Quick Start

If you are an experienced developer familiar with the technologies in this stack, getting started should be a breeze. The steps below are likely all you need to begin. If you need more assistance, refer to the other pages in this tutorial section for detailed setup instructions.

# Video Tutorial (Full Video)
 <div className="video-responsive">
  <iframe width="100%" height="100%" className="h-full w-full" src="https://www.youtube.com/embed/3qjy48Xidyg?si=W-hUdgH-6fW0menj" title="YouTube video player" frameBorder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerPolicy="strict-origin-when-cross-origin" allowFullScreen></iframe>
</div>

# Written Instructions
## Steps

### 1 - Download the Alpaca Stack Template
If you haven't already, the first step is to go to your members dashboard (Paid members only) and use the form on the page to request access to our repository. Once you have access, run:
```bash 
git clone https://github.com/moore-media-llc/alpaca-stack-ts-template-pro.git
```


### 2 - Install Packages
Navigate to the project folder in your terminal and install the NPM packages:
```bash
npm install" lang="bash"
```


### 3 - Create Environment File
In the root of the application, there is a file called `env.example`. Either create a copy (recommended) named `.env` or rename the file to `.env`.

### 4 - Add Environment Variables

- **Database**
  - `DATABASE_URL`: Set up a Postgres database (e.g., [Neon.tech](https://neon.tech/) or [Supabase](https://supabase.com/)) and paste the connection string here.
  - `DIRECT_URL`: Paste the same connection string as above. Some database services require both strings.

- **User Authentication (NextAuth)**
  - `AUTH_SECRET`: Run the command `openssl rand -base64 32` in the terminal and paste the output here.

- **Optional Auth Providers:**
  - GitHub
    - `GITHUB_CLIENT_ID`: Create an app on GitHub [tutorial](https://authjs.dev/getting-started/authentication/oauth) and paste the client ID here.
    - `GITHUB_CLIENT_SECRET`: Using the same app, paste the client secret key here.
  - Google
    - `GOOGLE_CLIENT_ID`: Create an app on Google [tutorial](https://authjs.dev/getting-started/authentication/oauth) and paste the client ID here.
    - `GOOGLE_CLIENT_SECRET`: Using the same app, paste the client secret key here.

- **Email:**
  - `RESEND_API_KEY`: Create an account and generate an API key at [Resend.com](https://resend.com) and add it here.

- **File Storage:**
  - `AWS_ACCESS_KEY_ID`: Create an account at Backblaze, generate a bucket and API keys. Place the "KeyID" here.
  - `AWS_SECRET_ACCESS_KEY`: Place the "applicationKey" here.

- **Stripe:**
  - `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY`: Create an account at Stripe.com and place the publishable key here.
  - `STRIPE_SECRET_KEY`: Using the same Stripe account, place the secret key here.
  - `STRIPE_WEBHOOK_SECRET`: Place the production webhook secret key here.

### 5 - Create Stripe Products
In the Stripe dashboard, go to [Product Catalog](https://dashboard.stripe.com/products) and create your Stripe products. Ensure they are duplicated in both production and test mode.

### 6 - Generate Prisma Client and Sync Database
With the correct database connection string in `.env`, go to the terminal and run:

```bash
npx prisma generate
```

Then, run:

```bash
npx prisma db push
```

This will create all the tables in your database. Check your database application or the web app to see the changes.

### 7 - Fill Out Site Config
In the root of the application, there is a file called `site-config.ts`. It's a JavaScript object with a bunch of key-value pairs. Fill it out. The keys are self-explanatory.

### 8 - Add Admin User
By default and for security, there is no setting in the front end or UI of the app to assign a user as an admin. This must be done in the database. Go to the database and navigate to the **User** table. In the **Role** column, switch it from "User" to "Admin". This will allow you to see the `/admin` path in your application.

### 9 - Test Application
After completing these steps, register for an account at `/register` and test the application.

**Things to test:**
- **User Authentication:** Go to `/register`, `/login`, `/reset` to test the primary authentication forms.
- **Social Authentication:** Log in with all social providers in the register/login forms.
- **Email:** While you should have received emails when registering for an account, you can also test the email integration with the `/contact-us` form. For local testing, use the email you registered with Resend.
- **File Storage:** Go to `/admin`, then `/admin/media`, and try uploading a small image file. If it uploads, your application works with your database and Backblaze.
- On the homepage, you will see the pricing section. If you set up your products correctly, everything should display as expected.

