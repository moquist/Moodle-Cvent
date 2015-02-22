Moodle-Cvent

Sponsored by:
    United States Baha'i National Center: http://american.bahai.us/

Supported Moodle versions:
    * 2.0+

Introduction:
    If you're a Cvent customer and you've got access to their integration API,
    this enrollment module allows you to get new and updated user accounts and
    enrollments from Cvent.

    The code is designed to make the best possible use of their API, attempting
    to get all (but only) the necessary data to keep moodle up-to-date while
    using the smallest possible number of API calls. (Cvent limits the number of
    calls that can be made within a 24-hour period.)

    This has been developed specifically for one client, but the hope is that
    others will also find this to be useful. Comments, questions, and patches
    are welcome!

Installation:
    Rename this directory to 'cvent', and copy it into your own moodle under the
    "enrol" directory. Then go to http://yourmoodle.tld/admin/ in your browser.
    This will create the DB tables. Then go to
    http://yourmoodle.tld/admin/settings.php?section=manageenrols to enable the
    Cvent module and configure its settings.

    You MUST be a Cvent customer with access to their API service, because:
    
    1. in the settings page you'll need to enter the authentication information
       (username, account number, and password) they give you for their API, and
    2. you must contact Cvent (or use their administration panel) and give them
       your server's IP address so they can add it to their whitelist.

    If you have any authentication errors (such as "INVALID_LOGIN"), please be
    sure both of these things have been done.


Dependencies:
    You must have the PHP xmlrpc and curl libraries installed on your system.

    If you're running Ubuntu, for example, you can probably get these by running
    the following commands in a terminal:
    $ sudo apt-get install php5-xmlrpc php5-curl
    $ sudo /etc/init.d/apache2 restart

Synchronizing:
    This plugin uses Moodle's cron() feature to synchronize regularly.

    Each execution of the cron() for this enrolment plugin should use no more
    than 8-12 Cvent API calls, unless you have more than 10k updates in between two
    runs of this script.

    CLI: Execute php enrol/cvent/cli/sync.php

TODO:
    * add configuration settings that determine how user provisioning works
        * how do we check for pre-existing accounts?
        * how do we set username/password for new accounts?
    * document how user provisioning and enrollment handling work

Matt Oquist <moquist@majen.net>
Updated Sat May 18 15:23:37 EDT 2013
