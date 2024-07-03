---
sidebar_position: 5
---

# Setup Auth / OAuth

Alpaca Stack comes with built-in user authentication using NextAuth. It supports traditional username and password logins as well as various provider options like Google and GitHub.

Personally, I prefer the classic username and password method for all my applications. Users are familiar with it, and it doesn't require them to sign up for another service to log in.

# Video Tutorial
### Setup Next Auth Secret Key
In this video I go over how to generate the Next Auth secret key to use Next Auth in the Alpaca Stack boilerplate template.
<div className="video-responsive">
<iframe width="100%" height="100%" src="https://www.youtube.com/embed/JhRbx7LCUM8?si=JmiWBG8ADlo1LLq5" title="YouTube video player" frameBorder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerPolicy="strict-origin-when-cross-origin" allowFullScreen></iframe>
</div>

### Setup Github OAuth
In this video I go over how to setup Github Oath to work with the Alpaca Stack boilerplate template.
<div className="video-responsive">
<iframe width="100%" height="100%" src="https://www.youtube.com/embed/h_k4D_-kfXQ?si=3-VsNkrvIhmJEffc" title="YouTube video player" frameBorder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerPolicy="strict-origin-when-cross-origin" allowFullScreen></iframe>
</div>

### Setup Google OAuth
In this video I go over how to setup Github Oath to work with the Alpaca Stack boilerplate template.
<div className="video-responsive">
<iframe width="100%" height="100%" src="https://www.youtube.com/embed/hNckXJWkaTY?si=hwoEklPevfmjVsTb" title="YouTube video player" frameBorder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerPolicy="strict-origin-when-cross-origin" allowFullScreen></iframe>
</div>

# Written Tutorial

### About NextAuth

**What:** NextAuth.js is a comprehensive open-source authentication solution for Next.js applications. It offers a straightforward and secure way to add user authentication and authorization, supporting a wide range of authentication providers (e.g., Google, GitHub, Facebook) along with email/password and custom authentication strategies.

**Why:** Building authentication from scratch can be complicated and time-consuming. NextAuth.js simplifies this by providing a highly configurable and extensible system, reducing development time while ensuring robust security. This allows developers to focus on building core features of their applications rather than dealing with authentication complexities.

Given its complexity, this boilerplate template includes NextAuth to ease the setup process. For more details, refer to the official documentation [here](https://authjs.dev/getting-started).

## 2. Environment Variables

To set up the default username and password login with NextAuth, follow these steps:

1. Open your terminal and run the command: `$ openssl rand -base64 32`. This generates a secure key.
2. Copy the generated key and paste it into the `AUTH_SECRET` environment variable in your `.env` file.

## 3. Setting Up Providers (Optional)

NextAuth allows you to integrate multiple login providers like Google, Facebook, and GitHub, making it easy to add login buttons for each provider.

For detailed instructions on setting up each provider, check out the comprehensive documentation provided by Auth.js [here](https://authjs.dev/getting-started/authentication/oauth).

