Architectural choices
=====================


Local dev, with remote, production-like staging
-----------------------------------------------

This can give great security and performance to your WordPress development site, 
by hosting it on your own computer.

By incorporating a staging environment, which closely mirrors your production site 
hosting, you can have more peace of mind and extra quality control steps to minimize 
errors creeping into your live site.

 
.. uml::

  partition "Your computer" {
    Deploy --> "staging"
    Deploy --> "production"
  }

  partition "Staging environment" #LightSkyBlue {
    "staging" --> "staging.yourdomain.com"
  }


  partition "Production environment" #CCCCEE {
    "production" --> "www.yourdomain.com"
  }

Due to the plugin's functionality involving a lot of URL rewriting, it's ideal to 
match your staging server's URL scheme with your production site's, to further 
mitigate risks of unexpected errors. So, if you're hosting your production site on 
a naked/apex domain like https://example.com, then you should have another domain 
with the same format, such as https://testexample.com. Likewise, if you're intending 
to serve your live site from https://www.example.com, then using another subdomain, 
such as https://wpdev.example.com may be prudent.

Whilst replicating every part of your production hosting environment to staging may 
cost more time and money, that's up to you to decide how much risk to take.


===========================================   ===== 
Pros                                          Cons  
===========================================   ===== 
As secure as your local workstation           Remote teams can't collaborate 
Full power of your local workstation          Some embedded scripts may not load on localhost
Allows for extra QA step before going live    Connection may be slower when deploying
===========================================   =====

Remote dev, with remote, production-like staging
-----------------------------------------------

When you have multiple workers contributing to the one WordPress site, then a local 
dev environment is unlikely to work. So, this takes the local dev environment example 
from above and replaces your local workstation with a remote machine (ie, VPS), 
available to multiple people.

By incorporating a staging environment, which closely mirrors your production site 
hosting, you can have more peace of mind and extra quality control steps to minimize 
errors creeping into your live site.

 
.. uml::

  partition "Remote dev server" {
    Deploy --> "staging"
    Deploy --> "production"
  }

  partition "Staging environment" #LightSkyBlue {
    "staging" --> "staging.yourdomain.com"
  }


  partition "Production environment" #CCCCEE {
    "production" --> "www.yourdomain.com"
  }

Due to the plugin's functionality involving a lot of URL rewriting, it's ideal to 
match your staging server's URL scheme with your production site's, to further 
mitigate risks of unexpected errors. So, if you're hosting your production site on 
a naked/apex domain like https://example.com, then you should have another domain 
with the same format, such as https://testexample.com. Likewise, if you're intending 
to serve your live site from https://www.example.com, then using another subdomain, 
such as https://wpdev.example.com may be prudent.

Whilst replicating every part of your production hosting environment to staging may 
cost more time and money, that's up to you to decide how much risk to take.


============================================   ===== 
Pros                                           Cons  
============================================   ===== 
Multiple workers can collaborate on the site   Requires more security than local workstation
Allows for extra QA step before going live     Usually requires additional cost for the server
Connection may be faster when deploying                                                
============================================   =====

Remote or local dev, without staging
-----------------------------------------------

Identical to the 2 examples above, but without the staging server for extra QA.  

An example of a remote development environment, without staging environment. 

.. uml::

  partition "Remote dev server" {
    Deploy --> "production"
  }


  partition "Production environment" #CCCCEE {
    "production" --> "www.yourdomain.com"
  }

This may be fine for most sites, but one must accept the risk of deploying straight 
from their dynamic WordPress development site to a static site in production. 
Without the static staging site, potential issues in going from dynamic to static 
may be missed.


============================================   ===== 
Pros                                           Cons  
============================================   ===== 
Faster process without staging                 Less quality control measures
============================================   =====

Dev site and static site on same server
---------------------------------------

This is what to **avoid**! 

Whilst technically possible to host your development WordPress site on the same 
server as you static site, it is strongly discouraged, as you'll lose the security 
benefits of isolating your development site from your live website.

A non-public development server may block many malicious requests, you could still 
be prone to DDoS style attacks, which could overload your server and bring down your 
live site. A non-malcious user mistake or any required downtime to your development 
server could have the same effect - taking your live site offline.

For this reason, it is advised to separate your development site from your live static 
site hosting.

