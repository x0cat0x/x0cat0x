---
layout: post
title: Local webserver access permission
subtitle: Local webserver access permission
tags: [apache]
comments: true
---


macOS Mojava - Apache - localhost - 127.0.0.1

Open the file /etc/apache2/httpd.conf 

Look for the code block

```
<Directory "/Library/WebServer/Documents">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.4/mod/core.html#options
    # for more information.
    #
    Options FollowSymLinks Multiviews
    MultiviewsMatch Any

    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   AllowOverride FileInfo AuthConfig Limit
    #
    AllowOverride None
   

    #
    # Controls who can get stuff from this server.
    #
    Order allow,deny
    Allow from all

</Directory>
```

With this configuration, your web sever is accessable from your computer itself and from all other computers in LAN network.

To restrict the access to your web server to just your computer, change the config to
```
    AllowOverride All
    
    #
    # Controls who can get stuff from this server.
    #
    Order allow,deny
    Deny from all
    Allow from 127.0.0.1
    
 ```
 then restart the apache
 
 ```
 sudo /usr/sbin/apachectl restart
 ```
