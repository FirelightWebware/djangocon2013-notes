# Trial by Fire: Real World Performance Optimization

_Speaker: Joseph Jasinski_


**more than 100ms bothers users**


## My site is slow... where do I start?

It's not usually a quick solution.

1. Find problems in the front-end. Possibilities: large and unoptimized 
   payloads. Large quantity of blocking requests. Slow responses from 3rd
   party resources. Use chrome developer tools to analyze requests. Or you
   can use an external application, such as Google PageSpeed Insights, 
   Pingdom's Speed Tools, Yslow Browser Plugin.
2. Finding problems on the back-end. Large quantity of SQL queries, or complex
   queries, performing unnecessary actions in the request/response cycle.
   Use django-debug-toolbar to inspect queries and view other metrics. Also
   you can extend it with additional plugins, look for Cache Panel and
   Template Timings. There is also profiling middleware you can install.

## Improving Performance

### Front-end

- HTML Minification, remove whitespace from your HTML. Always test your pages
  after installing to make sure the minification doesn't break anything. It
  will increase CPU time, but decrease network load.
- Combine and compress javascript and CSS. Use django-compressor with stuff
  like CSSTidy, CSSmin, JSMin, Slimit, Closure Compiler, YUI. CSSmin is easy
  to install.
- Optimize images -- remove metadata. Keep them below 70kb. Offer WebP to
  supported browsers. Use thumbnails instead of full images with something
  like easy-thumbnails. Use sprites when possible, especially images used
  frequently throughut site.
- Resource order - put critical stuff first.
- Lazy Loading - don't download image for the bottom of the page until the 
  user scrolls down there. Especially useful for long web pages.
- Use an asset CDN - serves assets from closest server, reduce load from
  server, but note that each alternate domain used requires a DNS lookup and a
  round-trip.

### Back-end

- Use "values\_list" when possible so Django doesn't query all model props.
- Don't be afraid to write raw SQL.
- Verify you aren't running the same query twice
- Use select\_related when you know you will need related data and Django will
  make fewer queries. But don't use it willy-nilly.
- prefetch\_related works similarly
- cache... how? which backend? generally use memcached, but redis works well
  too. low-level caching gives you the most control. prime your cache.
  template fragment caching is nice, and accepts context variables.

### CDNs

Browsers support ~6 connectionsper hostname. You could host on multiple CDNs to
maximize the number of requests the browser can do. But each host is an 
additional DNS lookup, so measure it.

### Limiting what you do inside of a request

Always ask yourself "do I really need to do this in this moment?" and if the
answer is "no", defer it (with e.g. celery or redis queue).

### Headers

Set the expires and cache-control headers. You can set a far-future expires on
files served by django-compressor because the url changes each time you change
the static files.

### Gzip

Gzip your content with the gzip middleware in Django or by setting it in your
apache or nginx config file. But for now don't gzip https responses because
there is a security leak.

### Other

Look into Google ModPage speed (?). Database connection poolers reuse db
connections. Don't use db for sessions... move to redis or memcached.

## Questions

Cache invalidation for template fragment caching -- there is a package you
can install to get cache keys for these so you can invalidate them. (Google
for it)

You can use PIL to create sprites from user-generated image content, and create
a long or wide image where all the pieces are the same height or width and you
can programmatically determine the position of the correct slice.

