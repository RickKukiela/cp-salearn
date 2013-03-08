cp-salearn
==========

Spam/Ham reporting for Spam Assassin's Bayesian Filters - For use on cPanel servers running Exim.

SUPPORT
=======
This script is provided as is, without support. Please do not email me for help.


HOW IT WORKS
============
You must decide the name of the imap folders you are going
have your users place their spam and ham training emails into. The default
setting is ReportSpam and ReportHam. Assuming you go with the defaults,
each IMAP user must create two IMAP folders on their account named accordingly.
When a user receives a spam mail they should move it to their ReportSpam folder
and when they receive a ham mail, they should COPY it to the ReportHam folder.

Please keep in mind that this script will EMPTY the report folders for each user,
every single time it runs (every hour unless cron is changed to run less often). Make
sure users know NOT to move ham messages and only copy them or they will lose
their emails once this script runs.


INSTALL INSTRUCTIONS
====================
1. Place this script inside your home directory.
2. chmod 755 cp-salearn (make executable)
3. Add ONE of the following crontab entries:
	(MAKE SURE YOU DO THIS AS THE USER THAT OWNS THE ACCOUNT AND NOT ROOT!)

	# CRON ENTRY WITH EMAIL LOG ENABLED:
	@hourly /path/to/cp-salearn

	# CRON ENTRY WITH EMAIL LOG DISABLED:
	@hourly /path/to/cp-salearn >/dev/null 2>&1

4. Teach your users to set up their report folders and how to use them.
5. Complete configuration section inside the cp-salearn script