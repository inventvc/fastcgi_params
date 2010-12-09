Nginx + FastCGI + PHP Params
============================

* *Author: Brendon Crawford*
* *Sponsored By: [Last.vc](http://last.vc)*
* *Format: Git Flavored Markdown*


Usage
-----

To use this file you must set the $remote_root variable. Here is an example
nginx server config which connects to remote FastCGI/PHP servers.

    upstream site_example_com {
        192.168.1.1:9000;
        192.168.1.2:9000;
    }
    server {
        listen 192.0.32.10:80 default;
        server_name example.com www.example.com;
        location ~ \.php$ {
            set $remote_root /var/www/example.com;
            fastcgi_pass site_example_com;
            fastcgi_index index.php;
            include fastcgi_params;
            break;
        }
    }


