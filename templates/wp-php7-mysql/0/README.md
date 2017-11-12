# WordPress PHP7 MySQL

One-click WordPress w/ PHP7-FPM, Redis, Nginx

## With MySQL

Includes a MySQL container - use the other catalog item to use an remote database.

## Volumes

Though it is not necessary to expose, a volume can be created at `/var/www/html` to access WordPress files.

## NFS Backup and Restore

Backup and restore can be enabled via Rancher NFS volumes.

### NFS Setup

1. Ensure NFS storage driver is available via `rancher-nfs`
1. Create an NFS volume named `backup`
1. Create WP stack with the settings:
    - "Remote Storage Driver" set to `rancher-nfs`
    - "Hostname" set to the domain name of the site

When the stack first starts, it will create a directory inside the `rancher-nfs/backup` directory with the name of the FQDN hostname. If the hostname is `site.com`, the directory name will be `backup/site.com` within the `rancher-nfs` storage driver.

### File Backup Behaviour

The `mysql-helper` container will handle backup and restore inside of this directory. It will backup files in a `.tar.gz` archive - 3 copies will be stored at 1-day intervals.

### Database Backup Behaviour

The `mysql-helper` container will handle backup and restore inside of this directory. It will backup files in a `.sql.gz` archive - 3 copies will be stored at 1-day intervals.

### Restore Behaviour

If `.tar.gz` or `.sql.gz` files are present when the `/var/www/html` directory does not have a restore timestamp file, `mysql-helper` will extract and import the archive files.

#### Creating Archives

The file archive will place the top-level archive files in the target directory. To ensure that your site files are at the top of the archive, use the `-C` flag when compressing: `tar -zcv backup.tar.gz -C ./mysite.com/`

#### Alternative: Specify `ARCHIVE_ROOT_FILE`

If an archive has files that are not at the top level, the `ARCHIVE_ROOT_FILE` environment variable can be specified to declare what _should_ be the website root. Setting this to a unique file at the web root of the site (ie. `wp-config.php`, `README.md`) will cause the restore tool to extract files in the directory of the given file.
