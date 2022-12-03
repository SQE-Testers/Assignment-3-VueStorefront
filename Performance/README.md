
# Usage of Cache

Caching is a temporary storage mechanism that allows websites to load information faster. Instead of accessing the database directly, the website will access the cached version and pull the necessary information from the server memory.

Cached data are files, scripts, images, and other multimedia stored on your device after opening an app or visiting a website for the first time. This data is then used to quickly gather information about the app or website every time revisited, reducing load time.

### Vue Storefront Architechure

![Vue Cache](https://i.imgur.com/jK8Yvjz.png)

The cache can and should be enabled on all Vue Storefront layers: including client (Service Worker), vue-storefront-api (nginx output cache) and vue-storefront app (SSR output cache).

### SSR Output Cache

Vue Storefront supports a very efficient Server Side Rendering cache. In this mode, the generated HTML pages are fully stored in the Redis cache. The cache entries are then tagged with all the products, categories (and potentially other data entities) used to render that specific page.

Let’s say the Category page contains 20 products products = [{ id: 120, ... }, { id: 324, ... }, ...] after this specific category page got rendered, Vue Storefront would tag the output cache entry with the following tags: P120, P324, C56 (… if the category id was 56).

Each time, Vue Storefront indexers (both: mage2vuestorefront and magento2-vsbridge-indexer) are pushing the changes for any of the tagged product to Elastic storage, the indexer is calling an URL like: https://your-instance.com/invalidate?tags=P120. This request invalidates cache, assigned to this specific product. There is no risk the user will get any outdated product information.

### API output cache

Although the SSR cache is pretty cool — even when it’s enabled, the cache hit ratio still would be pretty low. It’s because most of the requests are executed in CSR (client-side mode), querying the API directly from the client's browser. If you’re facing any Elastic performance issues or it’s high on resources that you’d like to limit— it’s a time to introduce the API output cache.

We’re recommending to put an nginx or varnish proxy in front of vue-storefront-api. With such a proxy, adding the API cache is pretty easy.

     location /api/ {
            proxy_pass https://vue-storefront-api:8080/api/;
        }

..

    location /api/catalog/ {
            proxy_pass https://vue-storefront-api:8080/api/catalog/;
            proxy_cache static;
            proxy_cache_valid 200 1h;
            proxy_cache_methods GET HEAD POST;
            proxy_cache_key "$scheme$proxy_host$request_uri|$request_body";
        }


# CDN 

The last mile to the customer is the most important. You can have the fastest servers, but if you distribute your page across geographic locations, it can't be fast. In our cloud, we use the fastest CDN solution provided by Cloud.

To improve site performance, Vue Storefront uses Google Cloud CDN which supports modern protocols initially developed at Google, like HTTP/2 and QUIC. Thanks to them, Google Cloud CDN enables websites to serve millions of requests per day seamlessly, taking care of delivering superb user experience across all touchpoints.



![Vue CDN](https://i.imgur.com/dwEyTlV.png)


## Use HTTP2 Push 

HTTP2 Push is a performance technique to reduce latency by loading resources even before the browser knows it will need them.
First, the browser will load and parse index.html. While parsing, it will find information about styles.css and script.js, sending a request to the server to get them. Because we know that the page needs those two files, we can use HTTP2 Push to send them to the client immediately without waiting for the client to request them.

    function pushScripts(): void {
        this.options.render = merge(this.options.render, {
            http2: {
            push: true,
            pushAssets: (request, response, publicPath, preloadFiles) => {
                return preloadFiles
                .filter(({ asType }) => asType === 'script')
                .map(({ file, asType }) => `<${publicPath}${file}>; rel=preload; as=${asType}`);
                }
            }
        });
    }


# Usage of Lazy loading

Lazy loading is a technique used to prevent or delay the loading of non-critical resources until they are needed. You can use this mechanism for different types of resources, but in the case of images, our goal is to lazily load everything that is not visible to the user within the initial viewport.

Use the loading="lazy" attribute to load an image lazily. It also works for the <nuxt-img> component.

    <img src="..." loading="lazy">
    <nuxt-image src="..." loading="lazy" />

Example of Lazy Loading in Vue Storefront:

https://github.com/vuestorefront/vue-storefront/blob/0f1eac70cf57ddb8b47d077596bea879cf28f591/packages/nuxt-theme-module/theme/components/SearchResults.vue#L76

# Usage of PWA
Progressive Web Application (PWA) is a type of web app that can operate both as a web page and mobile app on any device. It is a great solution for poor mobile UX and low conversion rates in your online store. Using standard technologies, PWA is aimed at delivering native-like user experience, with speedier conversion and cleaner browsing even with a poor Internet connection. 

The Nuxt. js PWA module registers a service worker for you to deal with offline caching. It automatically generates a manifest.json file. It automatically adds SEO friendly meta data with manifest integration. It automatically generates app icons with different sizes.

Vue Storefront uses Nuxt.js modules for PWA functionalities:

- [`@nuxtjs/pwa`](https://pwa.nuxtjs.org/) - for PWA functionalities.

#### Installation

Add @nuxtjs/pwa dependency to your project:

    npm i --save-dev @nuxtjs/pwa

Edit your nuxt.config.js file to add pwa module:

    {
        buildModules: [
            '@nuxtjs/pwa',
        ]
    }

# Usage of Service Workers

Web Workers are a simple means for web content to run scripts in background threads. The worker thread can perform tasks without interfering with the user interface. Once created, a worker can send messages to the JavaScript code that created it by posting messages to an event handler specified by that code (and vice versa).


![workers](https://i.imgur.com/wRF3fpO.png)

The main thread creates the worker using the “Worker” constructor. This constructor takes in a single argument, the path to the worker file. The worker file contains the code that will run in the worker thread; workers run in another global context that is different from the current window.

Data is passed between the worker and the main thread via messages — the main thread and worker thread sends messages using the postMessage() method, and respond to messages sent using the onmessage handler.


# Use of Local storage

Local storage can store 5MB of data per app for the lifetime of the app. Closing the browser will not affect the data in any way – it stays there unless you delete it.

You can only access the local storage object through localStorage. The methods you can use to perform operations on the localStorage object are:

    localStorage // to access the localStorage object 
    localStorage.setItem('name', 'John') // sets name equal to john localStorage.getItem('name') // "John" 
    localStorage.removeItem('name') // removes name from the localStorage localStorage.clear() // clears the localStorage

localStorage.setItem() takes a key and value as parameters and sets a new item in the local storage object equal to the given key value pair.

localStorage.getItem() takes a key as a parameter and returns the value stored to that key in the storage.

localStorage.clear() clears the whole localStorage object.

localStorage.removeItem() takes in a key as a parameter and removes the corresponding key-value pair. ‌‌

Any item that you store in localStorage will be stored as a string. This means that you need to convert other data types such as arrays or objects to strings – otherwise you lose their structure.

See the example below:      

    const scores = [10, 8, 6, 3, 9] 
    const scoresJSON = JSON.stringify(scores) 
    localStorage.setItem('scores', scoresJSON) 
    localStorage // output >> {scores: '[10, 8, 6, 3, 9]', length: 1}

In the example above, we first created an array score, then converted it into a string using JSON.stringify(), and finally saved the stringified scores array in localStorage.

![workers](https://i.imgur.com/Sa2Uzha.png)



# Reference

- https://vuestorefront.io/blog/caching-on-production

- https://www.nexcess.net/blog/what-is-redis-cache/

- https://docs.vuestorefront.io/cloud/v2/in-a-nutshell/features.html#multi-regions

- https://www.fmeextensions.com/blog/best-cdn-for-magento/

- https://docs.vuestorefront.io/v2/performance/optimizing-images.html

- https://vuestorefront.io/pwa

- https://pwa.nuxtjs.org/setup/

- https://www.freecodecamp.org/news/how-web-storage-works/
