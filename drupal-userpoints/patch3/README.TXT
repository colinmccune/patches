# Project
Drupal

# Module
User Points

# Issue
792944

# Issue Summary
On my site I generated user's rank which is based off their and everyone else's current points and I noticed that the userpoints.points field doesn't have an index on it. In my case this drastically speeds up performance and for me at least is worth the extra space taken up by adding the index.

I've attached a patch incase the module author thinks this would be useful for others as well. I could see this situation cropping up for anyone that is building Views that apply restrictions (where clauses, etc) based on a point threshold or building custom modules based on userpoints.

# Patch
userpoints.install.add_points_index.patch

# References
http://drupal.org/node/792944