## **XA** Check what is and if you are using it in your system without knowing it.


In short XA is a way to continue a transaction, not finish by an application.

More information may be found here http://en.wikipedia.org/wiki/X/Open_XA

Doing work as DBA Oracle, at my first job. We did an upgrade of our windows 2000 servers, at the same time a migration of a 10T database has been performed.

The Storage was the best that the money was able to buy, 3 nodes and ofcourse a true64 OS.

The performance was really slow and the applications started to create, dead locks, a work around was put in place. (a little script that detect a possible dead lock and kill the session), **YES** a bad killer script, but the system was able to perform work again. 

After two weeks of problems and checking at the database, the DBA started to read about Windows, the reason was simple, databases don't create dead locks, the applications do.

Reading the first page, was a recomendation from Microsoft, please use XA if you are able, reading about XA,sound a nice way to manage transactions. 

The schock was that Windows 2000 have this feature disabled, but Windows 2003, comes with this feature enabled (Sadly this feature comes enabled or enabled). 

so I did another ugly work around, I created a service that uses one node, so each Application server did end using one node (two nodes for the normal workload) and the last node for backups and batch work. **Sound familiar ?** 

I am sure this approach are the current configuration for several implementations that use Oracle RAC.

**Remember**

If all the nodes started to Lock the same record and the **SAME** session ID is the one doing the lock, I am sure you are using XA without knowing that. 

As Oracle RAC means HA at database level and parallel query across the nodes, the DBA needs to know XA and the developers needs to know XA, why ? 

Things may go really wrong if each other are not sharing the pain. The manager will see problems, at what level ? apps and Oracle, the manager may end moving from one technology into other because no one did read about XA.

And as I mention before,I think this is the real reason why Oracle RAC is failing in several implementations in the market.

Other spect to keep on mind is Oracle move from bonding for the Cluster Interconnects into something called HAIP, what is this ? 

Is just different networks, if you have four channels (Ethernet), HAIP will create four sub-nets, in short better performance less pain for the network team and Oracle running happy.

If you wish to know more about why, I will explain that in my next post, all is about performance and HAIP delivers a better performance for Oracle RAC. 