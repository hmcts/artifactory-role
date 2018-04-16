Artifactory
===========

Warning!
========

This role makes disk changes, and should only be run against a box built for purpose.

The box in questions should have a preconfigured LVM setup for root, and a new (blank) disk.

The blank disk will be used for everything else.

Before running this role, the user is advised to read the embedded back snipped (in `tasks/lvm.yml`) and understand what is going on.

What is this repo?
==================

This is the role used when installing Artifactory in the legacy reform setup.

It's quite bespoke, as it covers the likes of disk-configuration.

Bits and pieces could potentially be useful going forward.

When to run?
------------

This role should be run on a vanilla box with a large second disk, prior to it being enabled for use.

It can be run subsequently, but may restart Artifactory with certain changes.

Updating License
================

* Put your new license in Vault.
* Update the vars in AM (external repo) with the new date of expiry.

Testing
=======

To test SELinux and disk changes, you can copy `molecule.yml-vagrant` over `molecule.yml` and perform your tests. This can probably be done using flags inline too.

It will only work if you have Vagrant and libvirt set up correctly.

Don't leave it in place, copy the docker one back once you've done your tests.

TODO: Update to Molecule2.

----

After Artifactory has been started once, the only way to change the configuration (without using API with auth etc which can be complicated by LDAP etc), is to update the file `/etc/opt/jfrog/artifactory/artifactory.config.import.xml` and then restart the service.

It does take a while to start back up which could be a slight issue.
