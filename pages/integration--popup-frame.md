---
title: Popup frame
permalink: /integration/popup-frame
---

## Security headers

To ensure that your content is safeguarded against [clickjacking](https://www.owasp.org/index.php/Clickjacking) we recommend using the HTTP headers, X-Frame-Options and Content-Security-Policy. In the case you have added preventive measures we check the embedded website before trying to serve the popup-frame in the Flipbook viewer. This ensures that we don't end up showing the enduser an error in the browser, if this site doesn't allow to be iframed we give the user an option to open the site in a new tab in the browser.

## X-Frame-Options

X-Frame-Options was the first countermeasure introduced against clickjacking, and have been implemented to some extend in the major browsers. When using this you must set it to `ALLOW-FROM https://viewer.ipaper.io/` if you don't have a branded domain, if you have a branded domain the part should of course reflect that domain.
One of the limitations with this header is that it isn't respected by Chrome (and they have clearly stated that it won't be in the future), and at the same time it doesn't give you the option of allowing iframing on several sites. To solve that issue you will have to refer to Content-Security-Policy.

## Content-Security-Policy

Applying Content-Security-Policy is a more complex task, as it can have implications on the content on your own site if not done correctly. If your only intent is to prevent clickjacking, the frame-ancestors directive can be applied without it having implications on your content. In the case of you not having a branded domain you should add `frame-ancestors 'viewer.ipaper.io'` and in the case of you using a branded domain then you should of course use your branded domain instead.
As of the specification for Content-Security-Policy version 2 and 3 the value of frame-ancestors override any value set in X-Frame-Options if those specifications have been implemented by the browser.

## Summary

As stated in the introduction the best prevention is to include both X-Frame-Options and Content-Security-Policy since we support a wide range of browsers and not all of them have implemented Content-Security-Policy.

## See also

[OWASP Guide to Clickjacking defense](https://www.owasp.org/index.php/Clickjacking_Defense_Cheat_Sheet)
