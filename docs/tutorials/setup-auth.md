---
sidebar_position: 5
---

# Setup Auth / OAuth

Alpaca Stack comes with built-in user authentication using NextAuth. It supports traditional username and password logins as well as various provider options like Google and GitHub. 

## Video Tutorial
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

## Written Tutorial

### About NextAuth

**What:** NextAuth.js is a comprehensive open-source authentication solution for Next.js applications. It offers a straightforward and secure way to add user authentication and authorization, supporting a wide range of authentication providers (e.g., Google, GitHub, Facebook) along with email/password and custom authentication strategies.

**Why:** Building authentication from scratch can be complicated and time-consuming. NextAuth.js simplifies this by providing a highly configurable and extensible system, reducing development time while ensuring robust security. This allows developers to focus on building core features of their applications rather than dealing with authentication complexities.

Given its complexity, this boilerplate template includes NextAuth to ease the setup process. For more details, refer to the official documentation [here](https://authjs.dev/getting-started).

### Setup Next Auth Auth Secret Key

To set up the default username and password login with NextAuth, follow these steps:

1. Open your terminal and run the command: `$ openssl rand -base64 32`. This generates a secure key.
2. Copy the generated key and paste it into the `AUTH_SECRET` environment variable in your `.env` file.

### Setup OAuth Providers (Optional)
NextAuth allows you to integrate multiple login providers like Google, Facebook, and GitHub, making it easy to add login buttons for each provider.

### Turning off Oauth
If you do not want users to register or login with OAuth like Github or Google, then you can easily hide it on the from displaying on the forms by heading over to the registration and login auth components and delete the code that says 'showSocial'

```typescript title="/app/(auth)/register/page.ts" 
const RegisterPage = () => {
    return (
        <div>
            <CardWrapper
                title="Account Registration"
                subtitle="This is where the journey begins!"
                backButtonLabel="Already have an account? Sign in here!"
                backButtonHref="/login"
                //highlight-next-line
                showSocial //remove this line or change to showSocial={false}
            >
                <RegisterForm />
            </CardWrapper>
        </div>
    )
}
```
```typescript title="/app/(auth)/login/page.ts" 
const LoginPage = () => {
    return (
        <div>
            <CardWrapper
                title="Login"
                subtitle="Welcome back"
                backButtonLabel="Don't have an account? Sign up!"
                backButtonHref="/register"
                showSocial //remove this line or change to showSocial={false}
            >
                <LoginForm />
            </CardWrapper>
        </div>
    )
}
```


### Setup Github OAuth
This will enable users to register and sign in to your app using Github login credentials on your website. 

1. Register and Sign in to [Github](https://github.com)
2. Settings > Developer Settings
![Settings](/img/github-oauth-1.jpeg)
![Developer Settings](/img/github-oauth-2.jpeg)
3. OAuth Apps > New OAuth App
![New Oauth App](/img/github-oauth-3.jpeg)
4. Register a new OAuth Application
![Oauth Info](/img/github-oauth-4.jpeg)
  - Callback URL: 
    - Dev Url: `http://localhost:3000/api/auth/callback/github`
    - Production Url: `http://yourwebsite.com/api/auth/callback/github`
5. Copy and paste Client ID to "GITHUB_CLIENT_ID"
![Github client id](/img/github-oauth-5.jpeg)
![Github client id env](/img/github-oauth-6.jpeg)

6. Copy and paste Client Secret to GITHUB_CLIENT_SECRET"

![Github client secret](/img/github-oauth-7.jpeg)
![Github client secret env](/img/github-oauth-8.jpeg)

### Setup Google OAuth

1. Register and Sign in to [Google Cloud Console](https://console.cloud.google.com/)
2. Create Project
![Google create project](/img/google-oauth-1.jpeg)
![Oauth create project 2](/img/google-oauth-2.jpeg)
3. Api & Services > OAuth consent screen
![Oauth consent screen](/img/google-oauth-3.jpeg)
![Oauth consent screen 2](/img/google-oauth-4.jpeg)
4. Create "External" config
![External](/img/google-oauth-5.jpeg)
5. App information
![App info](/img/google-oauth-6.jpeg)
  - Required fields:
    - App name: Your app name
    - App domain (homepage): Your app homepage url
    - Developer contact information: Your email
6. Create OAuth client ID
![Create client ID](/img/google-oauth-7.jpeg)
![Create client ID 2](/img/google-oauth-8.jpeg)
![Create client ID 3](/img/google-oauth-9.jpeg)
  - Required Fields:
    - Application type: Web application
    - Name: Your app name 
    - Authorized JavaScript origins: 
      - Development URL: http://localhost:3000 
      - Production URL: https://yourwebsite.com
    - Authorized redirect URLs: http
      - Delopment URL: http://localhost:3000/api/auth/callback/google
      - Production URL: https://yourwebsite/api/auth/callback/google
7. Copy and paste credentials
![Create client ID 3](/img/google-oauth-11.jpeg)
![Create client ID 3](/img/google-oauth-10.jpeg)
