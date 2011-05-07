
Welcome to Username Enumeration Prevention.

By default Drupal is very secure (especially Drupal 7). However, there is a way to exploit 
the system by using a technique called username enumeration. Both Drupal 6 and 7 have the 
security flaw but it is much worse for people using Drupal 6. This is because Drupal 6 does 
not have any built in brute force prevention. When an attacker knows a username they can 
start a brute force attack to gain access with that user.

Attackers can easily find usernames that exist by using the forgot password form and a 
technique called “username enumeration”. The attacker can enter a username that does not 
exist and they will get a response from Drupal saying so. All the attacker needs to do is 
keep trying usernames on this form until they find a valid user.

This module will stop this from happening. When the module is enabled, the error message will 
be replaced for the same message as a valid user and they will be redirected back to the login form.

Installing Views:

Place the entirety of this directory in sites/all/modules/username_enumeration_prevention
 
Navigate to administer >> build >> modules. Enable Username Enumeration Prevention.

