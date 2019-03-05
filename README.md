[![Build Status](https://travis-ci.com/IRMooBear/ansible.webmin.svg?branch=master)](https://travis-ci.com/IRMooBear/ansible.webmin)

Install Webmin
=========

Install Webmin and copy SSL certificates so browsers doesn't complain all the time.

This role automatically download, install and select the Bootstrap theme for webmin for lighter interface.

Dependencies
------------
This role install webmin from source from https://sourceforge.net.

Requirements
------------
Have your own SSL certificate files ready?

Role Variables
--------------

    webmin_source:
      Debian:
        source: https://prdownloads.sourceforge.net/webadmin/
        version: "1.900"
        name: webmin_1.900_all.deb
        checksum: md5:8a8ab138819756ac37a75d51ee8edfe3
      RedHat:
        source: https://download.webmin.com/devel/rpm/
        version: "1.903"
        name: webmin-1.903-1.noarch.rpm
        checksum:
        
Override this to update webmin binary install.        
    
    webmin_autostart: yes
    
Autostart webmin on system start
    
    webmin_copy_ssl_certificate: no
    
Boolean on whether or not to copy the SSL certificate files.
    
    webmin_ssl_key:
    
SSL Certificate key file path.
    
    webmin_ssl_certificate:
    
SSL Certificate file path.    

    webmin_ssl_ca:
    
SSL CA certificate and intermediate certificates chain file path.   

    webmin_theme: bootstrap
    webmin_additional_themes:
      -
        name: bootstrap
        filename: bootstrap.wbt.gz
        url: http://theme.winfuture.it/bootstrap.wbt.gz 
        
Download additional theme from the web and install it.  The variable webmin_theme will set default theme.        
  
Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { 
         role: irmoobear.install_webmin, 
         webmin_copy_ssl_certificate: yes, 
         webmin_ssl_key: mykey.key,
         webmin_ssl_certificate: mycert.crt
         webmin_ssl_ca: myca.pem
         }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
