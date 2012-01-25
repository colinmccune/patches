# Project
Drupal

# Module
User Points

# Issue
791868

# Issue Summary
Right now the max_points and last_update fields from the userpoints tables are not exposed to the Views module.

I needed these fields exposed for a project and I've attached a patch which adds the required logic to expose them.

# Patch
userpoints.views.inc.patch

# References
http://drupal.org/node/791868
http://drupal.org/node/1048946