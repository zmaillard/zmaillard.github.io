---
layout: default
title: Projects
---

These projects are pet prograomming projects of mine that I work on off and on in my free time.

Highway Sign Portal
-------------------
<{{ site.data.links.highwaysigns }}>

Over the 15 or so years I have owned a digital camera, I have taken a lot of pictures of road signs.  This site catalogs my signs by state, county, and highway.  My first iteration of this site was on the beta of Google AppEngine.  I found this a little too constricting for development, and converted it to a Django application.

The back-end is PostgreSQL running the PostGIS spatial extensions.  Additionally, I am running the GeoDjango extensions for managing spatial data.  A task queue based on Celery and Amazon SQS runs various nightly jobs, and async tasks.  The whole stack runs in Docker containers.  I have a container for the data base files, the database application, web application, and the web proxy.  I initially went with Docker because of its ease of deployment to a new server.

The images are stored in an Amazon S3 bucket.  When an image is uploaded, a task queue runs some image processing to generate thumbnails, and different size display images, and then uploads the whole file structure to Amazon S3.  I have around 15GB of pictures hosted there, and my bill for that is pennies.

At some point I will move the code into a public repository.  I have some API keys and what not that I need to strip out of the code first.


Official Idaho Highway Map Viewer
--------------------------------------
<{{ site.data.links.roadmaps }}>

I love to collect maps, and I especially love to collect official state highway maps.  As a Cartographer type, I tend to have access to large format scanners.  Over one weekend, I scanned all of my Official Idaho Highway Maps.  From there I registered the maps into a Transverse Mercator projection, which is what all of the maps appeared to be in.  I then used Tilestash to generate tiles of the maps.  My initial plan was to run Tilestache to serve the tiles.  However, due to the expense of having to stand up a server in the cloud, I decided just to generate the tiles all at once and host the website on the Amazon S3 Service.  The project is on my Github page.  Currently the only code out there is for the website.  I will also add the Tilestache configuration files and the scripts I used to generate the maps.