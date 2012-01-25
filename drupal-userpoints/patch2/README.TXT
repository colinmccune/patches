# Project
Drupal

# Module
User Points

# Issue
798286

# Issue Summary

(1) Added filter and sort handlers to the following date columns on the userpoints_txn table:
- time_stamp
- changed
- expirydate

(2) The code defining the userpoints_txn table was all using 4 spaces versus 2 spaces which is Drupal's coding convention. This was driving me a bit nuts so I've fixed it which is why the patch is hard to read. If you do a diff using a visual diff program it is easier to see the changes.

Patch was created against 6.x-1.x-dev (2010-May-12)

# Patch
userpoints.views.inc.patch

# References
http://drupal.org/node/791868
http://drupal.org/node/1048946