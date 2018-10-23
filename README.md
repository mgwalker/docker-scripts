Docker scripts

- **aws** - AWS CLI. Passes along [environment variables](https://docs.aws.amazon.com/cli/latest/userguide/cli-environment.html)
  if they're set. Injects `~/.aws` into the container so if you have
  credentials configured and saved, they'll get added. Alternatively, you can
  use `aws configure` to create them. Also injects the current directory into
  `/project` inside the container and sets `/project` as the container's
  working directory.

- **cf** - CloudFoundry CLI. Hooks up `~/.cf` in the container to bring your
  credentials along, or you can `cf login` to create/set them. Does most of
  the basic stuff, but does not support any Docker networking configuration.
