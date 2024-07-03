---
sidebar_position: 8
---

# Setup Email

By default, Alpaca Stack uses [Resend](http://resend.com) for sending emails. Resend offers an easy-to-use solution with a generous free tier and affordable paid options. It's flexible and can be switched out for another service if needed.

# Video Tutorial
In this video I cover how to setup email integration in the Alpaca Stack boilerplate template. Specifically using the third party service called Resend.
<div className="video-responsive">
<iframe width="100%" height="100%" src="https://www.youtube.com/embed/HxByDKw9_M4?si=mUSJnnu7E5w0q6ja" title="YouTube video player" frameBorder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerPolicy="strict-origin-when-cross-origin" allowFullScreen></iframe>
</div>


# Written Tutorial


## About Resend

Resend is a developer-friendly email API service designed to simplify sending transactional emails from applications. It provides a straightforward API that allows developers to integrate email functionality into their apps with minimal configuration and code. Resend handles the complexities of email delivery, ensuring high deliverability rates and managing technical details like SPF, DKIM, and DMARC.

The primary benefit of using Resend is its ease of use and reliability. Developers can quickly set up and send emails without worrying about the intricate details of email protocols or delivery issues. This allows them to focus on building their applications while relying on Resend to manage their email needs efficiently.

For more information, visit [resend.com](http://resend.com).

## Setting Up Resend Mail Settings

### 1. Sign Up

- Register or log in to Resend.

### 2. Create API Keys

- Once logged in, navigate to the “API Keys” section on the left sidebar.
- Create a new API key.
- Set the **permission** to **full access**; no domain is needed for local testing.
- Copy the generated API key and paste it into your **.env** file.

### 3. Edit site-config.ts

- In the site configuration file, you will see two email keys. By default, Resend sends test emails using `onboarding@resend.dev`. Do not change this.
- Ensure that the test emails are sent to the email address you used when signing up for Resend. When registering on your application, use the same email; otherwise, you won't receive authentication emails like registration or password resets.

### 4. Test with Contact Form

- Once everything is set up, go to [www.yourwebsite.com/contact-us](http://www.yourwebsite.com/contact-us) and fill out the contact form using the email associated with your Resend account. It should work as expected.

### 5. Troubleshooting

- If emails don't seem to send, ensure that all test emails are being sent to the email address you registered with Resend.
- To check error logs, go to your API key settings. If the API key is being used, you can view the logs. If there are no logs, the application might not be communicating with Resend correctly.


