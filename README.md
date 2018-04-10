Artifactory
===========

Warning!
========

This role makes disk changes, and should only be run against a box built for purpose.

The box in questions should have a preconfigured LVM setup for root, and a new (blank) disk.

The blank disk will be used for everything else.

Before running this role, the user is advised to read the embedded back snipped (in tasks/lvm.yml) and understand what is going on.

What is this repo?
==================

This is the role used when installing Artifactory in the legacy reform setup.

It's quite bespoke, as it covers the likes of disk-configuration.

Bits and pieces could potentially be useful going forward.

When to run?
------------

This role should be run on a vanilla box, prior to it being enabled for use.

It can be run subsequently, but may restart artifactory with certain changes.

Updating License
================

* Put your new license in Vault.
* Update the var in AM (external repo) with the new date of expiry.

Testing
=======

To test selinux and disk changes, you can copy `molecule.yml-vagrant` over `molecule.yml` and perform your tests.

It will only work if you have Vagrant and Libvirt set up correctly.

Don't leave it in place, copy the docker one back once you've done your tests.

----

After artifactory has been started once, the only way to change the config
(without using API with auth etc which can be complicated by LDAP etc),
is to update the file /etc/opt/jfrog/artifactory/artifactory.config.import.xml
and then restart the service

It does take a while to start back up which could be a slight issue.
