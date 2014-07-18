Kalabox Docker Build Manager
===========================

This directory provides configurations to pull and/or build Docker images which are to be available
to Kalabox sites.

This is only concept with the goal of allowing users to extend available images with this same
format outside of core.

## config.json

This file defines detail about each image. The following properties can be defined for each image:

- `title`: A human readable string.
- `name`: The Docker repo name. You may optionally append a tag here. i.e. `kalamuna/kalabox-proxy:tag`
- `description`: A brief description of this image.
- `role`: The role this image serves within the context of a site. (See roles below)
- `method': Use `build` or `pull`
- `source`: The directory of the Dockerfile (relative), URL to a git repo, or repo name for `pull`.
- `includes`: An optional array of files to be prepended to a Dockerfile before building. (for maintainability & caching benefits)

## Roles

Each image can fulfill a specific role a site running in Kalabox requires.

* data
* mysql
* nginx
* php
* proxy


