GoOSe Linux Tagging Process
===========================

.. note:: This is a draft. Please do not rely on this document.

Thinking through the process when we build up a release of GoOSe. The following is the tagging workflow for GoOSe Linux 6 (gl6). Minor releases will be represented as gl6.1, gl6.2, etc.

                                                        gl6-updates
                                                        |
  gl6-alpha-optional   ->     gl6-beta-optional    ->   --gl6-optional
  |                           |                           |
  --gl6-alpha                 --gl6-beta                  --gl6


Stage 1 - Pre Alpha -> Alpha
----------------------------

As packages get built, they will land in either gl6-alpha or the gl6-optional-alpha, depending on where they came from upstream. 

Once all packages are built, an Alpha release is composed from the -alpha tag.


Stage 2 - Alpha
-----------------------

Once a successful Alpha is composed, a nightly compose will be automated. Testing will occur to ensure certain constraints are met (ABI compliance, all packages from upstream are represented, etc). 


Stage 3 - Alpha -> Beta
-----------------------

Once all QA tests successfully pass, a Beta release will be composed. A mass retagging will occur to move all packages from the -alpha to -beta.


Stage 4 - Beta
--------------

The Beta release is announced and made available to the user base.  The main focus of Beta is to find any glaring integration or user issues that were not found during the QA process. If there are no blocker issues, this stage should last no more than two weeks.


Stage 5 - Release
-----------------

The final Beta release becomes the gold release when no blockers exist and the two week waiting period has expired. 
