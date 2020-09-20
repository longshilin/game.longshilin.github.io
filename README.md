# game.longshilin.github.io


## Architecture

```

                        GitHub                 Preview,         DNS,
                      +---------+              Redirect,        Cache,
                      | Actions |              Functions,       Security,
                      |         |              etc.             etc.
                  +---+----+----v-----+        +--------+     +------------+         +---------+
+--------+  Push  |        |          | Deploy |        |     |            |         |         |
| Author +-------->  main  | gh-pages +--------> Vercel <-----+ Cloudflare <---------+ Clients |
+--------+        |        |          |        |        |     |            | Request |         |
                  +--------+-----^----+        +--------+     +------------+         +----+----+
                                 |                                                        |
                   Github Repo   |                                                        |
                                 |           +----------+                                 |
                                 |           |          |                CDN              |
                                 +-----------+ jsDelivr <---------------------------------+
                                             |          |     Assets: Images, CSS, JS
                                             +----------+

```




# Plugins
- hexo-enhancer
- hexo-excerpt
- hexo-generator-feed
- hexo-generator-sitemap
- hexo-generator-searchdb
- hexo-generator-cdn
- hexo-next-utteranc