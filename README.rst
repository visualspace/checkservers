checkservers
============
Simple check script for HTTP with logging, email and SMS notification (through 
`Mollie <http://www.mollie.nl/>`_), which checks the availability of an internet connection before checking.


Requirements
------------
* CURL
* Mollie account (when SMS notification is used)

Getting Started
---------------
#. Copy the files in `etc` to the system `/etc/` directory.
#. Copy the files in `sbin` to `/usr/local/sbin/`.
#. Copy the `config.example` files to `config` in `/etc/checkservers/` and `/etc/sendsms/`, and edit them.
#. Add a cron job to execute the `checkservers` script at regular intervals (ie. 10 minutes).

Creating a MACOSX user
----------------------

# Enter the interactive directory editor
$ sudo dscl

# You can get an overview of the users using

/Local/Default > ls Group gid
/Local/Default > ls Users uid
... etc ...

# Create an User and a group: ("/Local/Default >" is the shell prefix)
# Read what the commands do before you copy/paste.

/Local/Default > create Users/_checkservers UserShell /usr/sbin/false
/Local/Default > create Users/_checkservers UniqueID 300
/Local/Default > create Users/_checkservers PrimaryGroupID 300
/Local/Default > create Users/_checkservers NFSHomeDirectory /var/empty
/Local/Default > create Groups/_checkservers
/Local/Default > create Groups/_checkservers PrimaryGroupID 300
/Local/Default > append Groups/_checkservers GroupMembership _checkservers

