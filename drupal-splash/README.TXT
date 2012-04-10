# Project
Drupal

# Module
Splash

# Issue
Splash page won't show when visiting the site from google

# Issue Summary
I ran into this issue as well and determined the problem. The Splash module has a check to see if the referer url matches the sites base url and when this is true it assumes the user is coming from an internal url and it doesn't show the splash page. While this is the desired behaviour the logic checks to see if the base url is contained in any part of the referer url which is what causes the problem. Urls coming from Google include the destination site url as a query paramater in the referer url and this triggers the internal condition.

Example of the referer url value when you click on a Google link going to http://www.yoursite.com

Eg: http://www.google.com/url?sa=t&rct=j&q=YourSite&source=web&cd=2&ved=0CDU...

I've included a patch which modifies the referer url check to only consider referer urls which start with the sites base url as internal urls.

# Patch
splash-referer-check-too-general-1336394-5280150.patch

# References
http://drupal.org/node/1336394#comment-5817994
http://drupal.org/node/1336394