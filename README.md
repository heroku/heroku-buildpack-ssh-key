heroku-buildpack-ssh-key
====

Add an ssh key to your build.

Adapted from [SectorLabs/heroku-buildpack-git-submodule](https://github.com/SectorLabs/heroku-buildpack-git-submodule).

## Usage

1. Add the buildpack to your Heroku app:

    ```
    $ heroku buildpacks:add https://github.com/heroku/heroku-buildpack-ssh-key.git -i 1
    ```

    Keep in mind that the buildpack order is important. If you'll specify this buildpack after your default one (e.g. `heroku/nodejs`) it'll not work. See [https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app) for details.

2. Set `BUILDPACK_SSH_KEY` to the private SSH key you want added:

    ```
    $ heroku config:set BUILDPACK_SSH_KEY=$(cat ~/.ssh/id_rsa)
    ```

The buildpack will save the SSH key to your build at `~/.ssh/id_rsa`.

