Workflows for WordPress static site generation
==============================================

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




Dev site and static site on same server
---------------------------------------

This is what to **avoid**!
