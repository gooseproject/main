Howto Rebuild an Operating System with Free Software
====================================================

.. caution:: This is a draft document, use at your own risk.

This document discusses the process and procedure taken to build and produce `GoOSe Linux <http://www.gooseproject.org/get-goosed/>`_. This document covers a large swath of projects across many different disciplines. Please make sure to read this documntation thoroughly before beginning. 

This documentation is provided as a model on how to build a binary compatible version of any modern enterprise Linux. Our goal is to keep this guide up-to-date. However, this guide is likely to be wrought with errors and inconsistencies. While we hope this guide will be helpful, we provide this guide AS-IS and take no responsibility for the actions you take while reading.

First things first, the prerequisites
-------------------------------------

To build GoOSe, we spent a good bit of time researching tools to help us obtain source code, build said source code, and turn builds into an operating system that is free and available for anyone to use.

Tools needed:

* A Linux system with at least 250GB of disk space
  * Preferrably 4-6 Linux systems, each with 250GB of disk space. These will be used to paralellize the RPM Building process.
* Source RPMs for **every** package required to build the OS
  * This requires not only the packages listed in a kickstart to build the system, but all of the dependencies as well
  * GoOSe uses the SRPMS available from ftp.redhat.com, generally speaking
* RPM Building Tools
  * If using Fedora 15, simply install fedora-packager
  * If using RHEL6, install rpm-build (possibly other packages will be required as well)
* Koji RPM building and tracking system - (https://fedorahosted.org/koji)
* Pungi Distribution compose tool - (https://fedorahosted.org/pungi/)
* Time and patience - Strangely enough, building an operating system isn't the simplest task ever. It will take time and you **will** need patience.

There are probably more things needed, updates accepted.

Getting the Source
------------------

As stated before, obtaining the source is important. GoOSe obtains the source by cloning the ftp.redhat.com site. We have sample scripts that do this work at https://github.com/gooseproject/Bootstrapping/blob/master/makefile. These are the steps taken to obtain and extract each srpm.

* wget all of the srpms from ftp.redhat.com
  * This includes the 6Client, 6ComputeNode, 6Server and 6Workstation directories
* Extract the spec, archive and any patches into the appropriate locations
  * The spec and patches should reside in a git repository on github
    * These files will reside in the appropriate branch to correspond to upstream (eg. EL6, EL6.1, EL6.2)
  * The archive is to be uploaded or stored in a lookaside cache
    * This lookaside cache and the git repository are used by Koji to build the binary RPMs
    * We use a lookaside cache to avoid storing binaries in git
    * github only allows 300MB of disk usage, thus binaries would easily exceed the allotted usage

Building the Builder, Koji
--------------------------

To enable systematic building of all of the packages needed to make GoOSe Linux, a reliable way need to be used to build RPMs. Enter Koji. Koji's entire job is to build the entire set of RPMS that will be included in the operating system. However, setting up Koji is a bit time consuming and does have its challenges. There are several things to consider when building Koji, most of which are covered in the `documentation <http://fedoraproject.org/wiki/Koji/ServerHowTo>`_. While reading these documents, please consider reading the tips and tricks below. These should help speed the process up some.

Authentication
^^^^^^^^^^^^^^

Currently, GoOSe is using SSL authentication. Kerberos is nice, but unless you have a kerberos environment setup already, it can be easily added later.  SSL certificates are easy to create. Keep in mind, though, that each individual will need a koji certificate and one for their browser. Automating this process should be straightforward.

Koji Builders
^^^^^^^^^^^^^

Koji has several parts which generally live on different systems. Kojihub is the main part, which passes control to the Koji builders. Koji **can** live on one system. Having several builders makes the workload light, especially when building a new release. In addition, Koji builders can be setup to build different arches. Right now, the GoOSe Koji instance only builds x86_64, though we should have a couple more builders very soon.

Bootstrapping and The Buildroot
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

One of the major things to get right is the buildroot. This is the ultimate component for bootstrapping Koji properly. Referring to the `Koji Server Bootstrap <http://fedoraproject.org/wiki/Koji/ServerBootstrap>`_ document is a good way to get started. This document does not, however, explain what should be in the buildroot. A buildroot in Koji is simply put, the minimal amount of rpms (with their dependencies resolved) required to build any package. Essentially, creating a buildroot will take the bulk of setup and configuration in Koji.

The GoOSe buildroot for the dist-g6-build tag is approximately 91 packages for binary and 25 for source.
