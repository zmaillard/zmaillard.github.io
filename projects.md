---
layout: default
title: Projects
---

These projects are pet hobbies of mine that I work on off and on in my free time.

Highway Sign Portal
-------------------
http://www.sagebrushgis.com

Over the 15 or so years I have owned a digital camera, I have taken a lot of pictures of road signs.  This site catalogs my signs by state, county, and highway.  My first iteration of this site was on the beta of Google AppEngine.  I found this a little too constricting for development, and converted it to a Django application.

The back-end is PostgreSQL running the PostGIS spatial extensions.  Additionally, I am running the GeoDjango extensions for managing spatial data.  The whole stack runs in Docker containers.  I have a container for the data base files, the database application, web application, and the web proxy.  I initially went with Docker because of its ease of deployment to a new server.

The images are stored in an Amazon S3 bucket.  When an image is uploaded, a task queue runs some image processing to generate thumbnails, and different size display images, and then uploads the whole file structure to Amazon S3.  I have around 15GB of pictures hosted there, and my bill for that is pennies.

At some point I will move the code into a public repository.  I have some API keys and what not that I need to strip out of the code first.


Official Idaho Highway Map Viewer
--------------------------------------
http://www.idahohighway.com

I love to collect maps, and I especially love to collect official state highway maps.


Highway Sign Viewer For Android
---------------------------------------------------------