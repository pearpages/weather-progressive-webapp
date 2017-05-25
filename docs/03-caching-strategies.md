# Caching Strategies

+ Cache first then network (app shell)
+ Network first then cache (data that gets udpated frequently, e.g. Game leader board data)
+ Cache Only (saving battery)
+ Network Only (analytics, .e.g.  Inventory and prices for ecommerce site)
+ Cache and Network Race
+ Cache then network (e.g. Social Media Timeline Data)

## Cache and Network Race

We ask for both in parallel.

Generally cache version will be faster, but then we update the cache.

## Cache then Network Race Example

```js
 app.getForecast = function (key, label) {
    var url = weatherAPIUrlBase + key + '.json';
    if ('caches' in window) {
      caches.match(url).then(function (response) {
        if (response) {
          response.json().then(function (json) {
            // Only update if the XHR is still pending, otherwise the XHR
            // has already returned and provided the latest data.
            if(app.hasRequestPending) {
                console.log('updated from cache');
                json.key = key;
                json.label = label;
                app.updateForecastCard(json);
            }
          });
        }
      });
    }

    // Make the XHR to get the data, then update the card
    app.hasRequestPending = true;
    var request = new XMLHttpRequest();
    request.onreadystatechange = function () {
      if (request.readyState === XMLHttpRequest.DONE) {
        if (request.status === 200) {
          var response = JSON.parse(request.response);
          response.key = key;
          response.label = label;
          app.hasRequestPending = false;
          app.updateForecastCard(response);
        }
      }
    };
    request.open('GET', url);
    request.send();
};
```

## Seperating Shell from Data

```js
var cacheName = 'weatherPWA-v1';
var cacheDataName = 'weatherData-v1';
```

### Fetch Update

```js
var dataUrl = 'https://publicdata-weather.firebaseio.com/';

self.addEventListener('fetch', function (e) {
    console.log('[ServiceWorker] Fetch', e.request.url);
    if (e.request.url.startsWith(dataUrl)) {
        e.respondWith(
            fetch(e.request)
                .then(function (response) {
                    return caches.open(dataCacheName).then(function (cache) {
                        cache.put(e.request.url, response.clone());
                        console.log('[ServiceWorker] Fetched&Cached Data');
                        return response;
                    })
                })
        )
    } else {
        e.respondWith(
            caches.match(e.request).then(function (response) {
                return response || fetch(e.request);
            })
        );
    }
});
```