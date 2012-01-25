# Project
Drupal

# Module
Munin

# Issue
906984

# Issue Summary
Great module. I was able to get the content statistics to work but had issues with "Currently logged in user" stats. After a bit of digging around I discovered that the type for the "curuser" variable was set to 'GAUGE ' instead of 'GAUGE' - note the trailing whitespace on the first one. For me at least this caused the errors bellow which prevented the graph from being generated.

munin-update.log "/var/lib/munin/domain.com/site.com-drupal_users-curuser-g.rrd": Invalid DS type
munin-update.log Unable to update /var/lib/munin/domain.com/site.com-drupal_users-curuser-g.rrd: opening '/var/lib/munin/domain.com/site.com-drupal_users-curuser-g.rrd': No such file or directory

My Drupal site runs on Debian Lenny which uses Munin Version: 1.2.6-10~lenny2 which is quite old so its possible future version of Munin strip off trailing whitespace so this issue doesn't happen.

I've attached a patch in case anyone else runs into this issue.

# Patch
munin.user.patch

# References
http://drupal.org/node/906984