# Manifest

+ Chrome
+ Opera
+ Firefox

## Validator

[https://manifest-validator.appspot.com](https://manifest-validator.appspot.com)

## Icons Recommended Sizes

+ 48x48
+ 96x96
+ 128x128
+ 192x192
+ 256x256
+ 384x384
+ 512x512

```json
```
{
    "name": "Weather",
    "short_name": "Weather",
    "start_url": "/index.html",
    "icons": [{
        "src": "/icons/icon-128.png",
        "sizes": "128x128",
        "type": "image/png"
    },{
        "src": "/icons/icon-144.png",
        "sizes": "144x144",
        "type":"image/png"
    }],
    "background_color": "#3E4EB8",
    "theme_color": "#2F3BA2",
    "display": "standalone",
    "orientation": "portrait"
}

## Add to Home Scren For Safari

### Icons

```
# in the root folder
/apple-touch-icon.png
```

or

```html
<link rel="apple-touch-icon" sizes="60x60" href="apple-60.png">
<link rel="apple-touch-icon" sizes="76x76" href="apple-76.png">
<link rel="apple-touch-icon" sizes="120x120" href="apple-120.png">
<link rel="apple-touch-icon" sizes="152x152" href="apple-152.png">
<link rel="apple-touch-icon" sizes="167x167" href="apple-167.png">
<link rel="apple-touch-icon" sizes="180x180" href="apple-180.png">
```

### Hide UI

```html
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
```

### Title

```html
  <!-- Otherwise title is the Webpage title tag content -->
  <meta name="app-mobile-web-app-title" content="Weather App">
```

### Altogheter

```html
<!-- Apple add to home screen safari on iOS -->
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="app-mobile-web-app-title" content="Weather App">
<link rel="apple-touch-icon" sizes="60x60" href="apple-60.png">
<link rel="apple-touch-icon" sizes="76x76" href="apple-76.png">
<link rel="apple-touch-icon" sizes="120x120" href="apple-120.png">
<link rel="apple-touch-icon" sizes="152x152" href="apple-152.png">
<link rel="apple-touch-icon" sizes="167x167" href="apple-167.png">
<link rel="apple-touch-icon" sizes="180x180" href="apple-180.png">
````