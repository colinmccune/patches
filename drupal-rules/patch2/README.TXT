# Project
Drupal

# Module
Rules

# Issue Summary
Number variable token type no longer working with Token 6.x-1.13

I just recently installed Token 6.x-1.13 and noticed that the "number" data type in rules was no longer showing up as a token replacement option. After digging around I saw that the Token module Rule's code now looks for a 'token type' flag to be set in rules_rules_data_type_info(…). If it is set to FALSE then the item wont show up as token replacement.

A while back I introduced a patch #674992 to expose Rule's number data type to the Token module and it looks like I missed this whole 'token type' variable which looks like it was added to Rules in #515608. Sorry about that.

Attached bellow is a patch which changes 'token type' => FALSE to 'token type' => 'number' for the number data type as it does have a proper token definition.

# Patch
numberfix.patch

# References
http://drupal.org/node/831610#comment-3140814