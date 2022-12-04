# Security Of VueStoreFront
To improve the security of Vue Storefront applications , they use the helmet 
#### Helmet 
(opens new window)security extension by default for Nuxt application and the Server Middleware.

Let's First Understand the concept of middleware
#### Middleware
Middleware is like a layer between any application and the Operating system.It facilitates the communication between OS and Application.
Middleware makes it easier for software developers to implement communication and input/output, so they can focus on the specific purpose of their application. It gained popularity in the 1980s as a solution to the problem of how to link newer applications to older legacy systems, although the term had been in use since 1968

### Helmet
Helmet is a collection of middleware functions that has http response headers. It can be used in different Node.js frameworks but it has been promoted to use mainly with Express.js. Basically, it is used to secure your http response headers. Since HTTP headers can leak sensitive information about the application, therefore, it is important to use the headers in a secure way.
Helmet uses different built in modules to secure HTTP Headers

- Content-Security-Policy
- Expect-CT
- X-DNS-Prefetch-Control
- X-Frame-Options
- X-Powered-By
- Public-Key-Pins
- Strict-Transport-Security
- X-Download-Options
- Cache control
- X-Content-Type-Options
- Referrer-Policy
- X-XSS-Protection

### HTTP Headers
HTTPS Headers are used to pass additional information from client to server through the help of request and response.

### Configuring Helment in Vue Store Front
Helmet is disabled by default. It can be enabled by using the helmet property in the @vue-storefront/middleware/nuxt module configuration. 

```bash
  // nuxt.config.js
export default {
  modules: [
    ['@vue-storefront/middleware/nuxt', {
      helmet: true
      // or
      helmet: {
        // ...configuration
      }
    }]
  ]
}
```

### Configuring Helmet in VSF Server Middleware 
Helmet is disabled by default. It can be enabled by using the helmet property in the middleware.config.js file. There are two options to enable it  one with with the default configuration and other is to pass an object to use your custom configuration.

```bash
// middleware.config.js
module.exports = {
  helmet: {
    // default configuration
    crossOriginOpenerPolicy: false,
    contentSecurityPolicy: false,
    crossOriginEmbedderPolicy: false,
    permittedCrossDomainPolicies: {
      permittedPolicies: 'none'
    }
  }
};
```

### Server MiddleWare URL
The URL of the Server Middleware can be obtained using using Nuxt environment parameters. The publicRuntimeConfig object in the nuxt.config.js file's middlewareUrl field can be changed.

### Reporting of Security vulnerability  of Vue StoreFront
Vue Store Front guides it's users to email them about any security vulnerability they found.They have provided an email on thier github repositry
You check this page from the link given below:
[Reporting Security vulnerability](https://github.com/vuestorefront/vue-storefront/security/policy)

Moreover they have a command which will generate a text file which you can email them

The command is :
git format-patch HEAD~1..HEAD --stdout > patch.txt
