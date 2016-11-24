<h1>Nginx-Friendly Registry</h1>

From [https://github.com/emcniece/rancher-catalog](https://github.com/emcniece/rancher-catalog)

This catalog item consists of Portus, MySQL, and the Docker Registry.

It is set up to be compatible with an external Nginx proxy, or as a standalone stack. The [Let's Encrypt Nginx Proxy](https://github.com/emcniece/rancher-catalog/tree/master/templates/letsencrypt-nginx-proxy/0) container is an excellent partner.

A single certificate set is used for Portus and the Docker Registry. Typically these files are `registry.crt` and `registry.key`, but if Let's Encrypt is used these files can be `fullchain.pem` and `privkey.pem` respectively.