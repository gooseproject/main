========================================
Colaboration With Other Rebuild Projects
========================================

Current draft:
##############
The GoOSe Project is only one of the enterprise Linux upstream projects. We are excited to work together with others in the EL rebuild space, and feel that there is plenty of room for separate but collaborative communities. The similarities in our goals should work for our mutual benefit. And the differences which exist should only strengthen us all.

So we need to answer this question:

   In what can we collaborate?

What follows are the results of a pretty free-form brainstorming session we had at one of the GoOSe Project's weekly meetings.

* Shared infrastructure
  
  Sharing certian pieces of infrastructure makes a lot of sense.
  
  * Upstream Sources Mirroring -- Although there are various places that one can find the upstream sources having another colaborative mirror for the various rebuild projects could be benifital.
  * Cross Project Backups -- Doing backups is difficult, if we spread out the load of backing up our repositories, scripts, lookaside caches, configuration files we could restore in the case of a catestrophic failure
  * Project Mirroring -- Distributing the final product of our efforts can be daunting as well. Again, being willing to mirror the ISOs or packages of the other projects will help make all the products better accessable.

* QA help

  * building/configuring non-shared infrastructure (installing QA systems/tools)
  * building QA test suite
  * Shared test suite
  * Cross-QA checks
    * ABI testing verification

* Documentation

There are many places where EL rebuild projects can easily collaborate. The first that comes to mind is in the documentation side. The fact that all of these distros share a common ancestor should lead to very similar processes.
There is a great need for documentation and how-to's. Sadly most documentation is woefully out of date. This is one place where the colaboration between the rebuild projects could be 

  * pool documentation (write it for multiple distros)

* Build related information

  * build order
  * package metadata
  * package content signatures
  * ABI compliance information

Why another rebuild project?
----------------------------

* How we benefit

  * process  and code
  * community
  * Forkability test (can you fork the project if we all walk away?)

* how they benefit
  * community
  * meetings, structure
  * updates
  * EL rebuild planet?

