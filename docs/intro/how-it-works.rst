How it works
============


.. uml::

  skinparam ranksep 20

  partition "Dev server" {
    "Install Static HTML Output plugin" --> Set deployment method
    --> Set Deployment URL
    --> "Start export"
  }

  partition "Static HTML Output" #LightSkyBlue {
    "Start export" --> "Detect WP URLs"
    "Detect WP URLs" --> Crawl URLs
    --> Post-process crawled URLs
    --> Deploy static site
  }


  partition "Static site hosting" #CCCCEE {
    "Deploy static site" --> Serve static site
  }

