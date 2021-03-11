# Content security policy

Content security policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks

## Why do we need CSP?

Web security is based on same-origin policy (SOP), which prevents a website from accessing data outside its own origin. In theory, this should be enough to ensure security, but the modern web requires sites to include lots of assets from external sources, such as scripts and other resources from content delivery networks (CDNs), Google Analytics scripts, fonts, styles etc

Attacks can range from [data theft](https://www.bbc.co.uk/news/technology-54931873) to malware

## Using CSP

To enable CSP, you need to configure your web server to return the `Content-Security-Policy` HTTP header

Configuring Content Security Policy involves adding the `Content-Security-Policy `HTTP header to a web page and giving it values to control what resources the user agent is allowed to load for that page. For example, a page that uploads and displays images could allow images from anywhere, but restrict a form action to a specific endpoint

## Writing a policy

A policy is described using a series of policy directives, each of which describes the policy for a certain resource type or policy area. A policy should include a `default-src` policy directive, which is a fallback for resources that don't have a policy specified

A policy needs to include a default-src or script-src directive to prevent inline scripts from running, as well as blocking the use of `eval()`. A policy needs to include a `default-src` or style-src directive to restrict inline styles from being applied from a `<style>` element or a style attribute. There are specific directives for a wide variety of types of items, so that each type can have its own policy, including fonts, frames, images, audio and video media, scripts, and workers.

An example of a `contentSecurityPolicy` being set in a node server:

```
contentSecurityPolicy: {
  directives: {
    defaultSrc: ["'self'", 'data:'],
    scriptSrc: ["'self'", "'unsafe-inline'", 'api.amplitude.com', 'data:'],
    styleSrc: ["'self'", "'unsafe-inline'", 'fonts.googleapis.com', 'fonts.gstatic.com', 'data:'],
    fontSrc: ['fonts.googleapis.com', 'fonts.gstatic.com', 'data:'],
    frameSrc: ["'self'", 'https://*.zopa.com'],
    workerSrc: ["'self'"],
    connectSrc: ["'self'", 'api.amplitude.com', 'https://*.zopa.com'],
  },
},
```

Policies include:

```
`default-src `is a fallback directive used to specify the default content policy for most of the source directives. Common uses include default-src 'self' to allow content from the current origin (but not its subdomains) and default-src 'none' to block everything that’s not explicitly whitelisted.
`script-src` is used to whitelist script sources. To allow scripts from the current origin only, use script-src 'self'.
`style-src` is used to whitelist CSS stylesheet sources. To allow stylesheets from the current origin only, use style-src 'self'.
`connect-src` specifies permitted origins for direct JavaScript connections that use EventSource, WebSocket, or XMLHttpRequest objects.
`object-src` allows control over the sources of plugins such as Flash. Note that you can also specify permitted plugin types using the plugin-types directive (unsupported in Firefox as of v76).
`img-src` lets you restrict image sources.
`font-src` specifies permitted sources for loading fonts.
`media-src` restricts origins for loading sound and video resources.
`child-src` is used to restrict permitted URLs for JavaScript workers and embedded frame contents, including embedded videos. In Level 3, frame-src and worker-src directives can be used instead to control embedded content and worker processes respectively.
`frame-ancestors` restricts URLs that can embed the current resource in <iframe>, <object> and similar elements.
```
