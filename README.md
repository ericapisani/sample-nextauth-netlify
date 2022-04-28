## NextAuth.js on Netlify Sample Project

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/localden/sample-nextauth-netlify)

_Sample created by [Erica Pisani](https://github.com/ericapisani) in the [Next.js Plugin for Netlify Repository](https://github.com/netlify/netlify-plugin-nextjs/tree/main/demos/next-auth). This sample is in its own repository to make deployment easier._

![Example of logging in with Netlify in a Next.js application](media/login-demo.gif)

This example project came from [`next-auth-example`](https://github.com/nextauthjs/next-auth-example) provided by the [NextAuth.js](https://next-auth.js.org/) and was modified to use Netlify as the authentication provider.

For more details on how to get set up and configured with various providers, [visit the original repository](https://github.com/nextauthjs/next-auth-example).

## Local testing

### Running the project

Within this project directory:

```
npm install
npm run dev
```

### Configuring your environment

Copy the .env.local.example file in this directory to .env.local (which will be ignored by Git):

```
cp .env.local.example .env.local
```

Add details for the [Netlify Provider](https://next-auth.js.org/providers/netlify), which will require you to [create a Netlify OAuth application](https://functions.netlify.com/example/handling-oauth-flows/).

## Configuring OAuth application

To create a Netlify OAuth application:

* Visit `https://app.netlify.com/user/applications`
* Click **New OAuth App**
* Enter an application name
* Enter a redirect URI
  * For the purposes of this demo application you would use `http://localhost:3000/api/auth/callback/netlify` for local testing.
  * Once the site is deployed to production, make sure to update the domain part to your real site URL.
* Save the application, and copy the value for **Client ID** as the `NETLIFY_CLIENT_ID` and the **Client Secret** as the `NETLIFY_CLIENT_SECRET` into your `.env.local` file within the project
  * If you're testing this on a deployed Netlify site, you'll need to set the environment variables as part of the `Site Settings > Build & Deploy > Environment` settings. You'll also need to generate a [`NEXTAUTH_SECRET`](https://next-auth.js.org/configuration/options#nextauth_secret) environment variable and set that for a production build. The variable can be a random value that you compute for your application.
  * If you are deploying from this template, you can specify the variables as you go through the deployment process.

For configuring additional authentication providers, see [the official documentation](https://github.com/nextauthjs/next-auth-example#3-configure-authentication-providers).
