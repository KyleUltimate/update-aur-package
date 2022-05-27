# Update AUR Package

A simple yet powerful action to automatically update your AUR package to the version you just tagged on github. Minorly tweaked variant of [ATiltedTree/create-aur-release](https://github.com/ATiltedTree/create-aur-release).

## Inputs

| Input                | Required | Description                                                   |
| -------------------- | -------- | ------------------------------------------------------------- |
| `version`            | `false`  | The version of the AUR package to update to, will automatically choose according to tag if not provided.|
| `package_name`       | `true`   | The name of the AUR package to update.                        |
| `commit_username`    | `true`   | The username to use when creating the new commit.             |
| `commit_email`       | `true`   | The email to use when creating the new commit.                |
| `ssh_private_key`    | `true`   | The SSH private key with access to the specified AUR package. |

## Example

```yaml
name: Publish

on:
  push:
    tags:
      - "cli-v*"

jobs:
  aur-publish:
    runs-on: ubuntu-latest
    steps:
      - name: Publish AUR package
        uses: KyleUltimate/update-aur-package@v1.0.6
        with:
          version: 127+221
          package_name: my-awesome-package
          commit_username: "Github Action Bot"
          commit_email: github-action-bot@example.com
          ssh_private_key: ${{ secrets.AUR_SSH_PRIVATE_KEY }}
```
