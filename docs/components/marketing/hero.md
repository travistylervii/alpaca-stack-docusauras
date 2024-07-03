---
sidebar_position: 2
---
# Hero Section

## Important things to remember

- In the tutorial there are many different ways do the same thing. For example for my database I like using Neon.tech, but you might prefer supabase.  With so many options I cannot provide walkthroughs for all of them so I only show you the primary (and sometimes secondary) way I do things and prefer. If you prefer a different method, software or service you are welcome to use your own.
Also I am always looking to increase my efficiency and productivity, so if have any suggestions on how I can improve send me a message on twitter here at https://twitter.com/travistylervii
- Update any node modules and packages at your own risk. Updating beyond the default versions that come with the boilerplate application may break the app. Only update if you know what you are doing.
- All default page routes and api routes are private out of the box. This is done by design for security and convenience. You can adjust make routes public in the site-config.ts file.

## File System

### App Root Folders
- **/actions:** Server side actions
- **/app:** App route folders and page files.
- **/components:** Where all the components go.
- **/constants:** Where constant data and objects go.
- **/data:** Where all the database fetch functions.
- **/hooks:** Client side react hooks
- **/lib:** Where all the reusable server side functions go.
- **/prisma:** All Prisma schemas (models) go here.
- **/public:** Public files for the front end of the app, like images and media.
- **/schemas:** Where the client Zod form schemas go.
- **/types:** Where all my resusable typescript types go.

### App Root Files
- **README.md:** Typical application readme file
- **auth.config.ts:** NextAuth Config. Change Auth Providers here.
- **auth.ts:** For NextAuth user authentication. Do not modify unless you know what you’re doing.
- **compoennts.json:** Default config file for ShadCN npm package. (Added when importing npm module)
- **env.example:** The example environment file.
- **middleware.ts:** All traffic is routed through this file first to basicly determine if its a public or private http route or api route. More info on this later.
- **next.config.mjs:** Default config file created by Next JS.
- **package.lock.json:** This file is a generated file in a Node.js project that ensures consistent dependency installation by locking the specific versions of installed packages and their dependencies.
- **package.json:** A file in a Node.js project that defines the project’s metadata, scripts, and dependencies.
- **postcss.config.js:** A configuration file for PostCSS that specifies the plugins and options used to process CSS.
- **tailwind.config.ts:** A configuration file for Tailwind CSS where customizations like themes, variants, and plugins are defined.
- **tsconfig.json:** A file in a TypeScript project that specifies compiler options and project settings for the TypeScript compiler.
- **site-config.ts:** A TypeScript file used to configure site-wide settings and constants. A good starting point for adjusting settings.
    
## App Routes

  Each app route serves a specific purpose and enclosed it parentheses () has its own specific layout. 

- **Marketing (`/app/(marketing)`):** This is what the non registered customers see. Most of it is self explanatory from its naming  conventions so I will not go into the details of each route.
- **Dashboard (`/app/(protected)/dashboard`):** A private dashboard for registered members.
- **Admin (`/app/(protected)/admin`):** A private dashboard for assigned admins. Admins must be manually changed in the database for a user.
- **Auth (`/app/(auth)`):** For all authentication related pages.
- **Utility (`/app/utility`):** For misc pages that do not fall into any other category. These pages

## Site-config.ts:

This is the backbone of the application. It has global settings and constants that effect every part of the application. 

Start by changing these key value pairs. All the other ones unmentioned in the file will be changes throughout the remaining of the tutorial. 

- **appName:** This is reflected in multiple parts of the app including the SEO metadata and copyright section at the bottom of the application.
- **appDescription:** The information in this setting is reflected in the footer section of the application.
- **keywords:** For SEO purposes.
- **primaryDomain:** Used in footer, SEO metadata and mail.
- **isUnderContruction:** This true / false boolean will display an under construction splash page to anyone not assigned the “ADMIN” role in the database.
- **isBlogPublic:** This true / false boolean is designed to redirect the /blog route to the homepage if turned off. This way, if you don’t need a blog on your site, your don’t need to worry about the path being live.
- **themeColor:** Right now the themes support light and dark colors, which can be configured in the global.css file.
- **email:** testEmail is for resend testing purposes and authEmail is the from email your authentication (registration, password reset) emails will be sent from.
- **routes:**
    - **publicRoutes:** Every route is private by nature, (INCLUDING API’s). This is where you define if the route is public for the non authenticated users to see.
    - **authRoutes:** Typically you will never modify this, but the routes in this array will redirect logged in users to the defaultLoginRedirect route which is set to “/dashboard” by default.
    - **apiAuthPrefix:** for auth purposes, this is the defined api route for auth. No need to change this.
    - **defaultLoginRedirect:** The redirection path that the user goes to after logging in.
- **fileStorage:** The bucket name and url for your file storage. Will be configured in the “Setup File Storage” tutorial page.
- **stripe:** This is where you define your stripe product / plan information. We will configure this in the “Setup Stripe” tutorial page.

# Themes & Styles

I go into more depth in the [Themes & Styles page](/features/themes), however I figured I would briefly mention it here. 

This application is setup mainly with ShadCN and ShadCN themes and styles CSS variables. 

You can configure these settings in `/app/global.css`
