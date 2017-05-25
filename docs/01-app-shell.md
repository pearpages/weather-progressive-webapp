# App Shell

## Intro

+ Service Workers
+ Web App Manifest File

> Service Workers are to Progressive Web Apps as XMLHttpRequest was to Ajax

---

## What it is

Separates the core App UI from the data.

+ Cache
+ Instant Loading

## What goes in the app shell?

+ HTML (some)
+ Javascript (some)
+ CSS (some)
+ Images (some)
+ None Data

## Storage methods

+ local storage (synchronous, not transactional)
+ caches object (asynchronous, fast, not transactional)
+ IndexedDB (asynchronous, fast, transactional, ugly API)
    + localForage
    + lovefield

> Webbrowser storeage is not permanent.