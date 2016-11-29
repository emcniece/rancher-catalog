#emcniece/rancher-catalog

A catalog for Rancher which currently includes:

- StriderCD
- Apt-Cacher-NG
- Let's Encrypt Nginx Proxy
- Nginx-Friendly Docker Registry
- LogRotate
- WhoAmI

Enable this catalog by browsing to your Rancher installation at `/admin/settings` and add https://github.com/emcniece/rancher-catalog as a new catalog entry.

##TODO

  - Get the rancher-compose for letsencrypt to set network mode for the nginx container to "Host" from the UI dropdown
  - Get the registry stack proxied properly
  - Get letsencrypt stack triggering restarts properly
    - Separate services into 3?
    - Investigate why 'nginx' container is not restarted on docker.sock
  - Convert docker-gen template to labels instead of variables
  - Add template field to letsencrypt rancher-compose
  - Test if proxy is correct for single-port services
  - Test if strider-cd stack adds smtp link properly on creation