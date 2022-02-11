# Nukeeper for GitHub Action

Following the archival of Nukeeper (see [issue](https://github.com/NuKeeperDotNet/NuKeeper/issues/1155)), this repository is now archived as well.

## Nukeeper

NuKeeper is a tool to automagically update NuGet packages in .NET projects with the supports for .NET framework and .NET Core. To find out more about Nukeeper check out the neighboring [NuKeeper](https://github.com/NuKeeperDotNet/NuKeeper) repository.

## This action

This action allows you to run `nukeeper`'s `repo` command for the current repository, which performs version checks and automatically generates pull requests for outdated packages.

## Usage
To use the action simply create a `nukeeper.yml` (or choose custom `*.yml` name) in the `.github/workflows/` directory.

For example:

```yaml
name: Update packages

on:
  schedule:
    # * is a special character in YAML so you have to quote this string
    - cron:  '0 0 * * 0'

jobs:
  update:
    runs-on: ubuntu-latest
    name: Update dependencies
    steps:
      - name: Nukeeper
        id: nukeeper
        uses: nukeeperdotnet/nukeeper-action@0.1
        with:
          token: "${{ secrets.NUKEEPER_TOKEN }}"
```

Where `NUKEEPER_TOKEN` is a secret configured under `YOUR_REPOSITORY/settings/secrets` page. To generate the access token for your repository please see [Github Help](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line) page.

### License
NuKeeper is licensed under the [Apache License](http://opensource.org/licenses/apache.html)
