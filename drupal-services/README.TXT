# Project
Drupal

# Module
Services

# Issue
File.save gives "Access denied"

# Issue Summary
Sorry to open this bug again but I think it would make more sense to use '#access callback' versus a '#access arguments'.

If you look at file.get and file.getNodeFiles in file_service.module you'll see that they make use of an '#access callback'. Inside file_service.inc you'll find three access callbacks one defined for each file.get [file_service_get_access()], file.getNodeFiles [file_service_get_node_files()], file.save [file_service_save_access()]. In the case of file.save [file_service_save_access()] it's just a wrapper for user_access('save file information') so while the current code (latest release) provides the same behaviour the comment on file_service_save_access() indicates that its behaviour could change in the future.

I'd say because the access callback is define and the other two methods use access callbacks for consistency we should stick with using the access callbacks. If you don't you could run into a security problem in the future if someone makes changes to file_service_save_access() assuming it is being used when it actually is not.

I've attached a patch applied to 6.x-2.1 (2010-May-12)

# Patch
file_service.module.patch

# References
http://drupal.org/node/789204#comment-2962812
http://drupal.org/node/801344