# Kenvue Corporate GTM Code
This document is a quick reference to implement the Global GTM Container across all Kenvue Corporate sites. For any questions regarding this content please contact Steven Rowe - srowe32@its.jnj.com

## HTML Code
Add the following snippet to every page inside the `<head>` tag as possible:

```html
<!-- Google Tag Manager -->
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-WSPHT2V');</script>
<!-- End Google Tag Manager -->
```

Additionally, add this snippet just inside the opening `<body>` tag:

```html
<!-- Google Tag Manager (noscript) -->
<noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-WSPHT2V"
height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
<!-- End Google Tag Manager (noscript) -->
```
