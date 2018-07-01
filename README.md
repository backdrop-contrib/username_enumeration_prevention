# Username Enumeration Prevention

| Branch | Build Status |
| ------ | ------------ |
| [8.x-1.x](https://www.drupal.org/project/username_enumeration_prevention/releases/8.x-1.x-dev) | [![CircleCI](https://img.shields.io/circleci/project/github/nicksantamaria/drupal-username_enumeration_prevention/8.x-1.x.svg?style=for-the-badge)](https://circleci.com/gh/nicksantamaria/drupal-username_enumeration_prevention/tree/8.x-1.x) |
| [7.x-1.x](https://www.drupal.org/project/username_enumeration_prevention/releases/7.x-1.x-dev) | [![CircleCI](https://img.shields.io/circleci/project/github/nicksantamaria/drupal-username_enumeration_prevention/7.x-1.x.svg?style=for-the-badge)](https://circleci.com/gh/nicksantamaria/drupal-username_enumeration_prevention/tree/7.x-1.x) |

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

## Get Started

### Composer

* Add the project to your project's composer dependencies.
    ```sh
    composer require "drupal/username_enumeration_prevention"
    ```
* Navigate to **Administer >> Extend**.
* Enable Username Enumeration Prevention.

### Manual

* Place the entirety of the module directory in
modules/contrib/username_enumeration_prevention.
* Navigate to **Administer >> Extend**.
* Enable Username Enumeration Prevention.

## Contribute

Development of this module takes place on [GitHub](https://github.com/nicksantamaria/drupal-username_enumeration_prevention).

* If you encounter issues, please [search the backlog](https://github.com/nicksantamaria/drupal-username_enumeration_prevention/issues).
* Please [create issues](https://github.com/nicksantamaria/drupal-username_enumeration_prevention/issues/new?labels=bug) and [feature requests](https://github.com/nicksantamaria/drupal-username_enumeration_prevention/issues/new?labels=enhancement) in GitHub.
* Even better, feel free to fork this repo and [make pull requests](https://github.com/nicksantamaria/drupal-username_enumeration_prevention/compare).
