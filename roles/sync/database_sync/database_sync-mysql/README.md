# Database sync - MySQL
Sync MySQL databases between environments.

In order to manipulate an AWS Autoscaling Group (ASG) your `deploy` user must have an AWS CLI profile for a user with the following IAM permissions:
* `autoscaling:ResumeProcesses`
* `autoscaling:SuspendProcesses`
* `autoscaling:DescribeScalingProcessTypes`
* `autoscaling:DescribeAutoScalingGroups`

<!--ROLEVARS-->
## Default variables
```yaml
---
mysql_sync:
  mysqldump_params: "{{ _mysqldump_params }}" # set in _init but you can override here.
  cleanup: true # if false leaves tmp database dump on deploy server for debugging purposes.
  archival_method: "gzip" # oprions are "bzip2" or "gzip".
  databases:
    - source:
        # Name of the database to take a dump from.
        database: "{{ project_name }}_prod"
        # Host that can connect to the database.
        host: "localhost"
        # Creds file on the host.
        credentials_file: "/home/{{ deploy_user }}/.mysql.creds"
        # This can be of types:
        # - rolling: (database backups). In that case we'll need build parameters.@todo
        # - fixed: "fixed" database name
        # - dump: Use an existing dump. In that case, the "database" variable is the absolute file path.
        type: fixed
        # For "rolling builds", so we can compute the database name.
        build_id: mybuildprod
        # Whether or not use to create a fresh database backup or use a nightly one.
        fresh_db: true
        # Location where nightly backups are kept. This must match the value set for cron_mysql_backup.dumps_directory. Below is the default.
        # This var is only used when fresh_db is set to "false".
        dumps_directory: "/home/{{ deploy_user }}/shared/{{ project_name }}_{{ build_type }}/db_backups/mysql/regular"
        # If the source is on an ASG, provide the ASG name here. Otherwise, leave empty.
        asg: ""
      target:
        database: "{{ project_name }}_dev"
        credentials_file: "/home/{{ deploy_user }}/.mysql.creds"
        # This can be of types:
        # - rolling: (database backups). In that case we'll need build parameters.
        # - fixed: "fixed" database name
        # - dump: Creates a dump file on the target server. In that case, the "database" variable is the absolute file path.
        type: fixed
        # For "rolling builds", so we can compute the database name.
        build_id: mybuilddev
        # If the target is on an ASG, provide the ASG name here. Otherwise, leave empty.
        asg: ""

```

<!--ENDROLEVARS-->

<!--TOC-->
<!--ENDTOC-->
