---
title: Why Static?
---

I’ve been really interested in static site generation, JAMstack, Hugo and Netlify for a while now. In fact, my previous personal website was written in Jekyll and hosted on GitHub pages.

At [Tomango](http://www.tomango.co.uk), I’ve just built our first production site using these technologies and needed a resource to pool together all the benefits of SSG for a meeting. A meta solution seemed to fit the bill.

Why Static? is a static site in Hugo that (at the time of writing) lists out a lot of benefits to SSG and Netlify. At this point, it’ll form a checklist of things to mention when explaining the concept to others on the team.

## What is the JAMstack?

The [JAMstack](https://jamstack.org/) is a methodology for building static websites using client-side JavaScript, APIs and prerendered Markup. It takes you from a purely static site to a 'dynamic' static site.

I love that the baseline is serving markup quickly. With all the JS frameworks in the world, this feels like a step in the right direction. Then JavaScript enhances that content, adding in functionality. Finally, APIs provide the heavier logic for features like comments, search and authentication. These can be custom or third-party.

## Features of the JAMstack

### Speed
Serving HTML files is really quick. After working in WordPress-land, you forget how quick the web is by default.

### No on-the-fly build
There's no PHP running. There is no backend. You don't have a custom rewrite rule matching up URLs to files. Just a classic folder structure that serves the web like it was 1995.

### No monolithic app
The world does not have to boot up to serve a page a-la WordPress.

### Hugely reduced attack surface area
When there's no backend, what's there to hack. Plugin vulnerabilities are no more. The server provider won't get angry if your CMS isn't up to date. Those custom rewrites are a really obvious entry point.

### Scales hugely if you get a hit
Last year we had a site getting 3k concurrent visitors and 135k visitors in one day and only then did Apache start to flinch. If that was a DB driven site, or a PHP site running at any level of complexity, our server would be taken down.

If the site manages to get a link from a national newspaper or becomes a 'hit', static is the only way to scale without a huge amount more infrastructure.

### Git-centric
All the content is stored in Git, along with the site and assets. Version controlling the content means reverting back to past states is a breeze. There's also no cost to having revisions unlike a traditional DB-driven site.

### Still dynamic, just moved up a level
'Static' is a deceiving term. When you think about our sites, most are really static. If you and I both load our company site up, we both see exactly the same thing. If you and I load up twitter.com, we see something totally different. Twitter is dynamic, the sites we build rarely are. They may be updated often, but they are still ultimately static.

With static site generators like Hugo, a new site can be built in a matter of seconds. So it can continue to feel 'dynamic', whilst having all the static benefits.

### Developer convinience
I built my own 'static' PHP library to give me the feeling of a CMS. Includes, partials and conditional rendering etc. As nice as writing pure HTML files, it's not practical, nor scalable to copy/paste the header and footer onto every page. A static site generator has a build step that can do things like pull in partials. You can even define overwritable blocks, create templates and work with JSON.

### Portability
A static site is portable, there are no server requirements. With everything stored in Git, moving to a new machine or setting up another developer is simple. The lack of a database or the reliance on a specific language is really refreshing.


## Netlify

### Fast
Netlify is really quick as it does one thing, serve HTML files.

### CDN
By building their network on CDNs, the website is served by a server that's really close to your location. Compare [this, a Rackspace server in Surrey](https://testmysite.io/5a5b5d8281987663d64cf448/tomango.co.uk), with [this, a Netlify CDN-served site](https://testmysite.io/5a5b5e2981987654e74cf476/hartwell.netlify.com). 

The TTFB difference around the world is astonishing. A 100ms score in Germany may be acceptable, but a 650ms score from Australia or USA is not. If your clients are global, a single server is not sufficient.

### Instant cache invalidation
There are two hard problems in Computer Science...

But seriously, caching is something we regularly overlook at the start of a project. It's only when we get to pushing a new feature does it become a problem. So we resort to butchering our files with hashes or dates, adding another complex step to the build process.

Netlify handles this with some Etag genius paired with HTTP2. They keep track of file hashes so you don't have to and your clients always see the latest version of the site, even on a global CDN.

### Scalable
CDNs are designed to soak up traffic surges.

### No FTP
I always felt that a clever deployment strategy was out of reach, something only the cool-kids and big projects needed. But that meant using FTP and dealing with all the frustrations, mistakes and speed downsides that come with it. Netlify preconfigures all the integrations that you could possibly need so you can forget Filezilla ever existed.

### Git integration
The big one. Whenever you push, Netlify builds and deploys. You can set it to build all branches, focus on the live branch leaving you to work on master, or anything in between.

### Pull request previews
Get a unique URL for every pull request to help you work with multiple developers. Netlify will automatically add a comment to each PR.

### Instant rollbacks
Make a mistake? Click a button to rollback to any point in time. 

### HTTP2
HTTP2 opens a multi-plexed connection between the server and browser meaning each asset request is substantially quicker, and can be run in true parallel.

### SPA prerendering
Get all the SEO benefits of a traditional site whilst keeping the user benefits of a single-page application.

### Language-based redirects
Let the CDN serve the correct language for the user.

### Best practises within minutes
Get all the current best practises without being a sysadmin.

### Post processing
Compress images & minify and concatenate JS and CSS at build time letting you write code and not worry about the tooling.

### Form-handling
One of the main reasons you build & host your own static library. Netlify gives you all the form handling backend for free, all you write is the form. They send the notifications, safely store the submittion and redirect the user on your behalf.

### Auth
Authenticate parts of the site - not so static afterall?!

### CMS
[Prose](http://prose.io/) and [NetlifyCMS](https://www.netlifycms.org/) both offer client-friendly editors. When a change is made, the service commits to the repository which triggers a build and deployment.

### Split testing
Proper AB testing on multiple branches lets you roll out new features incrementally or compare different landing pages with ease.

### Functions
Deploy AWS lambda functions within the repository for custom server-side coding.

___

Site by [Trys Mudford](http://www.trysmudford.com/)
