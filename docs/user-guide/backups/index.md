# Creating Backups

At a minimum, a backup of PhotoPrism should include the files in [your *originals* folder](../../getting-started/docker-compose.md#photoprismoriginals) and a copy of the index database. We also recommend backing up [the *storage* folder](../../getting-started/docker-compose.md#photoprismstorage) so that you don't need to recreate any thumbnail or sidecar files, and your backup includes the complete configuration.

!!! tldr ""
    The easiest way to create a full backup is to first run the backup command to generate a database dump as shown below.
    Then back up your *originals* and *storage* folders using any standard file backup utility.

## Scheduled Backups

By default, [PhotoPrism 240523-923ee0cf7](../../release-notes.md#may-23-2024) and newer versions automatically create daily database backups for you, with up to 3 copies being retained. The schedule, the type of backups, and the number of backups to be retained can be [changed in the configuration](../../getting-started/config-options.md#backup).

## Backup Command

You can run the following command [in a terminal](../../getting-started/docker-compose.md#command-line-interface) to manually create a new MariaDB or SQLite database backup:

```
docker compose exec photoprism photoprism backup -i -f
```

If you are using Podman on a Red Hat-compatible Linux distribution:

```
podman-compose exec photoprism photoprism backup -i -f
```

By default, a backup is created in `storage/backup/mysql/[YYYY-MM-DD].sql`. A custom backup base folder can be configured with [`PHOTOPRISM_BACKUP_PATH`](../../getting-started/config-options.md#storage)

Omit the `-f` flag if you do not want to overwrite existing files. You can also specify a custom filename as an argument (or `-` to write the SQL dump to [stdout](../../getting-started/advanced/backups.md)):

```
docker compose exec photoprism photoprism backup -i [filename]
```

Alternative ways to create SQL dumps from SQLite are shown in our [advanced backup guide](../../getting-started/advanced/backups.md#sqlite-backups).

!!! tldr ""
    Note that our examples use the new `docker compose` command by default. If your server does not yet support it, you can still use `docker-compose` or alternatively `podman-compose` on Red Hat-compatible distributions.

## Important Folders

### Originals

The [*originals* folder](../../getting-started/docker-compose.md#photoprismoriginals) contains your original photo and video files. You can back it up and restore it using any standard file backup program if you have not already set this up.

### Storage

SQLite, config, cache, backup, thumbnail and sidecar files are saved in [the *storage* folder](../../getting-started/docker-compose.md#photoprismstorage). As with the *originals* folder, the exact path on your computer [depends on your configuration](../../getting-started/config-options.md#storage).

We recommend that you back up this folder as well so that you don't need to recreate the thumbnails and have a complete backup of your configuration. As for the *originals* folder, you can use any standard file backup utility to do this.

!!! example ""
    Depending on the [resources available to us](https://www.photoprism.app/oss/faq), a future version may include additional features so that you do not have to rely on external tools to perform file backups and can use a web interface.
