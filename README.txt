Username Enumeration Prevention
===============================

By default Drupal is very secure (especially Drupal 7+). However, there is a
way to exploit the system by using a technique called username enumeration.
Drupal 6, 7, and 8 have this issue, though it is much worse for people using
Drupal 6.  This is because Drupal 6 does not have any built in brute force
prevention.  When an attacker knows a username, they can start a brute force
attack to gain access with that user. To help prevent this, it is best if
usernames on the system are not easy to find out.

This module provides several additional protections to prevent username
enumeration.

### Request New Password Validation

Attackers can easily find usernames that exist by using the forgot password
form and a technique called "username enumeration". The attacker can enter a
username that does not exist and they will get a response from Drupal saying
so. All the attacker needs to do is keep trying usernames on this form until
they find a valid user.

This module will stop this from happening. When the module is enabled, the
error message will be replaced with the same message as a valid user and they
will be redirected back to the login form. If the user does not exist, no
password reset email will be sent, but the attacker will not know this is the
case.

### Access User Profiles Permission

If a user belongs to a role that has "access user profiles" permission granted
to it, then that user can serially visit all integers at the URL
http://drupal.org/user/UID and get the username from the loaded profile pages.

Also With the "access user profiles "permission, the user can call the core
callback at http://drupal.org/user/autocomplete/a and get the usernames.
Replacing the "a" with each letter of the alphabet, prints an array of
usernames.

Installing this module on a site will notify site administrators whether this
issue is present or not, via the Status Report page (Home » Administration »
Reports » Status report).

### Other

Note: There may be other places where usernames could be exposed that this
module may not know about. Examples are the "submitted by" information on nodes
or comments, views, exposed filters or by other contributed modules. Users
looking to hide the usernames from comments and nodes should look at using
realname or some other tool.


Requirements
------------

none.

Installation
------------

- Install this module using the official Backdrop CMS instructions at
  https://backdropcms.org/guide/modules.

- This modile has no additional configuration.

Documentation
-------------

Additional documentation is located in the Wiki:
https://github.com/backdrop-contrib/backdropusername_enumeration_prevention/wiki/Documentation.

Issues
------

Bugs and Feature requests should be reported in the Issue Queue:
https://github.com/backdrop-contrib/backdropusername_enumeration_prevention/issues.

Current Maintainers
-------------------

- [Jen Lampton](https://github.com/jenlampton).
- Seeking additional maintainers.

Credits
-------

- Ported to Backdrop CMS by [Jen Lampton](https://github.com/jenlampton).
- Maintained for Drupal by [Nick Santamaria](https://github.com/nicksantamaria) and [other generous contributors](https://www.drupal.org/node/1150376/committers)
- Originally written for Drupal by [ToneUK](https://www.drupal.org/u/toneuk)

License
-------

This project is GPL v2 software.
See the LICENSE.txt file in this directory for complete text.
