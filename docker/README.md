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
- `method`: Use `build` or `pull`
- `source`: The directory of the Dockerfile (relative), URL to a git repo, or repo name for `pull`.
- `includes`: An optional array of files to be prepended to a Dockerfile before building. (for maintainability & caching benefits)

Maybe even items like `docker run` attributes could be defined in this config if there were any settings
that would vary per image.

## Roles

Each image can fulfill a specific role a site running in Kalabox requires.

* data
* mysql
* nginx
* php
* proxy

Data from all available `docker/config.json` files (however that ends up getting supported) would be combined
to provide users with options for which images will be used to make up a specific site.

## Builds

The builds should always support vanilla Dockerfiles, but the `includes` option would require the
Dockerfile to be dynamically built. It should be easy enough to handle the build in a temp directory
but the concept of a dynamic Dockerfile might be useful for pluggable/customizable features. It could
also be opening a kalibox of worms. :)


