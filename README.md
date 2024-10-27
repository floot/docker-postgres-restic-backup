# Docker Postgres Restic Backup

A sidecar docker container that backups a PostgreSQL database via restic to an S3-compatible storage.

The setup is surprisingly simple:

The docker image is based on alpine and executes the `backup` script daily via alpine's `crond` service.

## Environment variables

* `NOTIFY_URL`: URL that will be sent a notification to, after the whole backup process ends

The following environment variables have a mutually exclusive `*_FILE` counterpart that can be set to a path to a Docker secret.

* `PGHOST`: PostgreSQL server host
* `PGUSER`: PostgreSQL user name
* `PGPASSWORD`: PostgreSQL user password
* `PGDATABASE`: PostgreSQL database to backup
* `RESTIC_REPOSITORY`: Restic repository name
* `RESTIC_PASSWORD`: Restic repository password
* `AWS_ACCESS_KEY_ID`: S3 Access ID
* `AWS_SECRET_ACCESS_KEY`: S3 Secret Key
