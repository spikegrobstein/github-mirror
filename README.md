# GitHub repo mirror

This repo contains some scripts that will iterate over every repo that your GitHub account has access to and
clones them with `--mirror` so that one can have a full snapshot of everything their GitHub account has access
to.

## Why?

I created this after reading a post on reddit about a guy who had one of his repos put up for ransom by some
malware and then shortly after, GitLab posted in their blog about the rising occurances of incidents where
users are having their repos held for ransom. I realized that I didn't have any kind of backup of all of my
github repos, especially since they span so many years of work.

This is being up up as a public repo only so that others may take advantage of the work I put into this on
this sunday morning.

## Using it

### Prerequisites

These scripts depend on:

 * `bash 4.x` or newer
 * `git`
 * `hub` (https://hub.github.com)
 * `jq`  (https://stedolan.github.io/jq/)
 * `sponge` (usually from the `moreutils` package from your OS)

Make sure you have `hub` properly configured.

### Get started

    ./bin/do_backup <target-dir>

Pass the directory where you want the backup to write all of the repos. This directory will be created if it
doesn't exist and the scripts will create a `repos.json` file in that directory which defines all of the
metadata for that backup. In the `<target-dir>`, a directory will be created for each org/user that owns the
given repo and a `<name>.git` directory will be created inside with the mirrored repo.

### Example:

    ./bin/do_backup /path/to/backups

will create:

    /path/to/backups/
      repos.json
      org1/
        repo1.git
        repo2.git
      org2/
        repo3.git
        repo4.git
      ...

### Limitations and details

This also does a full clone of every repo using `--mirror` each time it's run. This means that it's going to
take roughly the same amount of time to run each time it's run as it's designed to create snapshots rather
than pulling changes since the last run.

