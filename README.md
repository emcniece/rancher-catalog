#emcniece/rancher-catalog

A catalog for Rancher which currently includes:

- Apt-Cacher-NG
- Concourse CI
- Let's Encrypt Nginx Proxy
- Logrotate
- Nginx-Friendly Docker Registry
- StriderCD
- Verdaccio NPM Proxy/Registry
- WhoAmI

Enable this catalog by browsing to your Rancher installation at `/admin/settings` and add https://github.com/emcniece/rancher-catalog as a new catalog entry.

##TODO

  - Add template field to letsencrypt rancher-compose
  - Test if strider-cd stack adds smtp link properly on creation