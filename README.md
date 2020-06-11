# Nukeeper for GitHub Action

This action allows you to run `nukeeper` repository command for the current repository.

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

Where `NUKEEPER_TOKEN` is a secret configured under `YOUR_REPOSITORY/settings/secrets` screen. To generate the access token for your repository please see [Github Help](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line) page.

### License
NuKeeper is licensed under the [Apache License](http://opensource.org/licenses/apache.html)
