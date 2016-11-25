# Node Wordpress Backup
Gulpfile to backup a Wordpress installation for migration.

## Installation
1. Clone to /exports
2. Execute `npm install` in /exports

## Usage
```ssh
gulp --dbhost <hostname> --dbuser <database username> --dbpass <database password> --dbdatabase <database name>
```

Example:
```sssh
gulp --dbhost localhost --dbuser wordpress --dbpass wordpress --dbdatabase wordpress --excludeDir ../wp-content/themes/mytheme/vendor/ --excludeDir ../wp-content/themes/mytheme/node_modules/ --oldDomain localhost --newDomain mywebsite.com
```

`exports/` will populate with the backup - an sql dump and an archive of the files.

To import the backup, create a database with the SQL dump, Configure wp-config.php and other configuration files.

## Commands

### Replace domain in database
```ssh
gulp --oldDomain localhost --newDomain mywebsite.com
```

### Archiver Option
Choose the archiver to use whem compressing the files. You have the option of zip and tar.gz. Zip can have problems with symlinks. If unzipping is failing use tar.gz.
```ssh
gulp --archive zip
```
Default: tar.gz

### Exclude Directories
Exclude a directory. Uses glob syntax.

Exclude all node_modules directories
```ssh
gulp --excludeDir **/node_modules
```

Exclude /node_modules and /wp-content/themes/mytheme/vendor
```ssh
gulp --excludeDir node_modules --excludeDir wp-content/themes/mytheme/vendor
```