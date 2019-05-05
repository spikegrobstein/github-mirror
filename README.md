# GitHub repo mirror

This repo contains some scripts that will iterate over every repo in your GitHub account and clone them with
`--mirror` so that one can have a full snapshot of all repos in their account.

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
metadata for that backup. Each repo will be written to a `<name>.git` directory in `<target-dir>` in a flat
structure.

### Limitations

The current version of this only clones the current user's git repos. It doesn't support pulling other repos
that the user may have access to or anything like that.

