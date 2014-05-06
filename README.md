nginx_proxy
========

Takes an existing nginx installation and simply adds nginx site configurations that proxy other services.

Requirements
------------

nginx must be installed. It doesn't matter how you did it.

Role Variables
--------------

In order to define a proxy site to be configured, you can use the following:

    server_name: nginx        # the servername to listen to
    server_port: 80           # the port your nginx proxy listens on
    site_root: /var/www       # site root, not sure if needed
    locations:                # these are the actual proxy locations
        - name: ghost blogging  # just for better orientation
          path: blog            # path of this location - empty for root
          proxy_pass: http://127.0.0.1:2368  # where to proxy to
          additional_settings: proxy_redirect off;proxy_buffering off;proxy_set_header X-NginX-Proxy true; # in case you need any other configs passed


Dependencies
------------

nginx, obviously. Other than that, there should be some services running you want to put a proxy in front of.

Example Playbook
-------------------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: yauh.nginx_proxy }

License
-------

BSD

Author Information
------------------

Stephan Hochhaus <stephan@yauh.de>

[yauh.de](http://yauh.de)