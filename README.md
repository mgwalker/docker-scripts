Docker scripts

- **7z** - 7-Zip. Injects the current directory into `/working` inside the
  container and sets `/working` as the container's working directory. Passes
  along arguments.

- **aws** - AWS CLI. Passes along [environment variables](https://docs.aws.amazon.com/cli/latest/userguide/cli-environment.html)
  if they're set. Injects `~/.aws` into the container so if you have
  credentials configured and saved, they'll get added. Alternatively, you can
  use `aws configure` to create them. Also injects the current directory into
  `/project` inside the container and sets `/project` as the container's
  working directory.

- **cf** - CloudFoundry CLI. Hooks up `~/.cf` in the container to bring your
  credentials along, or you can `cf login` to create/set them. Does most of
  the basic stuff, but does not support any Docker networking configuration.

- **cf_pg_dump** - Runs a `pg_dump` on the first database instance hooked up
  to a given app. Run with `cf_pg_dump <app name>`. Assumes you're already
  logged in and targeting the right org and space. Also assumes that there's
  at least one database, and that the first one is PostgreSQL. 😬 Outputs
  some status info to `stderr`, and the actual SQL dump to `stdout`.

  ```shell
  cf_pg_dump my-app > dump.sql
  ```
