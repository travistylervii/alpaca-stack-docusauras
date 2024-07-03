---
sidebar_position: 1
---

# Site config

This is the backbone of the application. It has global settings and constants that effect every part of the application. 
Start by changing these key value pairs. All the other ones unmentioned in the file will be changes throughout the remaining of the tutorial. 

## File Location
- /site-config.ts

## Config Settings
- **appName:** This is reflected in multiple parts of the app including the SEO metadata and copyright section at the bottom of the application.
- **appDescription:** The information in this setting is reflected in the footer section of the application.
- **keywords:** For SEO purposes.
- **primaryDomain:** Used in footer, SEO metadata and mail.
- **isUnderContruction:** This true / false boolean will display an under construction splash page to anyone not assigned the “ADMIN” role in the database.
- **isBlogPublic:** This true / false boolean is designed to redirect the /blog route to the homepage if turned off. This way, if you don’t need a blog on your site, your don’t need to worry about the path being live.
- **themeColor:** Right now the themes support light and dark colors, which can be configured in the global.css file.
- **email:** testEmail is for resend testing purposes and authEmail is the from email your authentication (registration, password reset) emails will be sent from.
- **routes:** Route settings for middleware.ts 
  - **publicRoutes:** Every route is private by nature, (INCLUDING API’s). This is where you define if the route is public for the non authenticated users to see.
  - **authRoutes:** Typically you will never modify this, but the routes in this array will redirect logged in users to the defaultLoginRedirect route which is set to “/dashboard” by default.
  - **apiAuthPrefix:** for auth purposes, this is the defined api route for auth. No need to change this.
  - **defaultLoginRedirect:** The redirection path that the user goes to after logging in.
- **fileStorage:** The bucket name and url for your file storage. Will be configured in the [Setup File Storage](/tutorials/setup-file-storage) tutorial page.
- **stripe:** This is where you define your stripe product / plan information. We will configure this in the [Setup Stripe](/tutorials/setup-stripe) tutorial page.
