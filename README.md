# Locale Buildpack

In order to reduce the stack image size, Scalingo's [base images](https://doc.scalingo.com/platform/internals/base-docker-image) don't include language packs by default.
You may still want to use a custom language pack though.

## Installation

```
scalingo env-set BUILDPACK_URL=https://github.com/Scalingo/multi-buildpack
```

Create a `.buildpacks` file at the root of your repository containing for instance:

```
https://github.com/Scalingo/locale-buildpack
https://github.com/Scalingo/ruby-buildpack
```

*Note that the second buildpack depends of your application, change it accordingly*

## Configuration

Create a `.locales` file at your app's root, with all the locales you need. Example:

```
de_DE
fr_FR
```

Commit that file and trigger a new build. The specified locales will be installed by the buildpack.

### Hacking

You can test this buildpack in a local docker container with the following command:

```
make compile
```

Then, to connect to the container:

```
docker-compose run test bash
```
