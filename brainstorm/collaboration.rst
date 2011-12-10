========================================
Collaboration With Other Rebuild Projects
========================================

Current draft:
##############
The GoOSe Project is only one of the enterprise Linux upstream projects. We are excited to work together with others in the EL rebuild space, and feel that there is plenty of room for separate but collaborative communities. The similarities in our goals should work for our mutual benefit. And the differences which exist should only strengthen us all.

So we need to answer this question:

   In what can we collaborate?

What follows are the results of a pretty free-form brainstorming session we had at one of the GoOSe Project's weekly meetings.

* Shared infrastructure
  
  Sharing certain pieces of infrastructure makes a lot of sense.
  
  * Upstream Sources Mirroring -- Although there are various places that one can find the upstream sources having another collaborative mirror for the various rebuild projects could be beneficial.
  * Cross Project Backups -- Doing backups is difficult, if we spread out the load of backing up our repositories, scripts, look aside caches, configuration files we could restore in the case of a catastrophic failure
  * Project Mirroring -- Distributing the final product of our efforts can be daunting as well. Again, being willing to mirror the ISOs or packages of the other projects will help make all the products better accessible.
  * Help Building and Configuring Non-Shared Infrastructure -- Most of these projects are using the same or similar tools, Koji for example. Working together on setting up these systems will help reduce the amount of constitutional knowledge(better phrase here?)

* QA help

  * Building QA Test Suites -- Due to the common ancestor of these projects, a common set of test cases could be useful. This should be extensible/fork able for the test cases which would be specific to a certain project.
  * Cross-QA Checks -- A very good way of testing if something is correct is having someone else run the same test as you. Sharing the QA work and results would reduce the need for everyone to figure things like this out for themselves. I think the best example of this would be the information needed to verify ABI compatibility.

* Documentation

Of the many places where EL rebuild projects can easily collaborate, the best return on investment is sure to come from the documentation side. Again the common ancestor of these projects works in our favor. There is a great need for documentation and how-to's. Sadly most good documentation is out of date. Thus a collaborative documentation effort would help lighten the load and keep things better up to date.

* Distribution Creation Information

  * build order
  * package meta data
  * package content signatures
  * ABI compliance information

* how we all benefit
  * community
  * meetings, structure
  * updates
  * EL rebuild planet?

