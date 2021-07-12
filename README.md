
Username Enumeration Prevention
===============================

Username enumeration is when a malicious actor can use brute-force techniques to
either guess or confirm valid user accounts in a system. When an attacker knows
a username, they can start a brute-force attack to gain access with that user.

In Backdrop, it may be possible to derive a username by visiting user profile
pages, or by using the password reset form (see below for details on each).

This module provides several protections to prevent username enumeration by
making usernames on the system harder to discover.

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

WARNING: By telling people that an email has been sent even when it has not, it
can create a very frustrating experience for those legitimately attempting to
recover a lost password.

### Access User Profiles Permission

If a user account belongs to a role that has "access user profiles" permission
granted to it, then that account can serially visit all integers at the URL
http://example.com/user/UID and may be redirected to a URL containing a valid
username.

Also With the "access user profiles "permission, the account can call the core
callback at http://example.com/user/autocomplete/a and get the usernames.
Replacing the "a" with each letter of the alphabet, prints an array of
usernames.

Installing this module on a site will notify site administrators whether this
issue is present or not, via the Status Report page (Home » Administration »
Reports » Status report).

### Other

Note: There may be other places where usernames could be exposed that this
module may not know about. Examples are the "submitted by" information on
content or comments, in views, in exposed filters or by other contributed
modules. People looking to hide the usernames from comments and content should
considder using the realname module, or some other tool.


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
