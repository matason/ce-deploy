# Roles
Ansible roles and group of roles that constitute the deploy stack.
<!--TOC-->
## [Config](cache_clear/README.md)
Cache clearing commands.
### [Drupal 8](cache_clear/cache_clear-drupal8/README.md)
Clear caches for Drupal 8.
### [Matomo](cache_clear/cache_clear-matomo/README.md)
Clear caches for Matomo.
### [Opcache](cache_clear/cache_clear-opcache/README.md)
Clear opcache.
## [CLI Tools](cli/README.md)
Roles to install app-specific cli tool and utilities (Drush, ...)
### [Drush](cli/cachetool/README.md)
Installs the `drush` command-line tool for the deploy user.
### [Drush](cli/drush/README.md)
Installs the `drush` command-line tool for the deploy user.
## [Composer](composer/README.md)
Performs a composer install on a freshly deployed codebase.
## [Config](config_generate/README.md)
Generates config files and handles sensitive variables.
### [Drupal 8](config_generate/config_generate-drupal8/README.md)
Generates settings.php file for Drupal 8.
### [Drupal 8](config_generate/config_generate-matomo/README.md)
Generates settings.php file for Drupal 8.
## [Cron](cron/README.md)
Roles to generate cron entries.
### [Database backup cron task](cron/cron_database_backup/README.md)
Ensure regular local backups of databases.
### [Database backup cron task - MySQL](cron/cron_matomo/README.md)
Ensure regular local backups of MySQL databases.
## [Data backups](database_backup/README.md)
Generate backups for each build.
### [MySQL backups](database_backup/database_backup-mysql/README.md)
Generate MySQL backups for each build.
## [Deploy](deploy_code/README.md)
Step that deploys the codebase.
## ["Meta"](meta/README.md)
Roles that bundles other individual roles together for tackling common use cases.
### [Drupal 8](meta/deploy-drupal8/README.md)
Role for deploying single Drupal 8 instances, or multisites with a single database.
## [Sync roles](sync/README.md)
Roles that sync data/assets between environments.
### [Database sync](sync/database_sync/README.md)
Roles that sync databases between environments.
<!--ENDTOC-->