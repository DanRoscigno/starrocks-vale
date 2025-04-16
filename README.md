## Overview

This repo contains rules for writing documentation for StarRocks. These rules are not complete, so please add to them by submitting PRs when things need to be added or changed. For now, the configuration for the CI check will be set to only report issues on lines that we edit in our PRs so that we can quickly get our PRs reviewed and merged. At some point when we have more time we will do some bulk editing.

> Note
>
> In VS Code and other editors you will see all of the potential issues and errors as you write. Fix these if you have time as you are editing other parts of the file, but errors on lines that you have not changed will not show up in the PR reviews at this time.


## Install Vale

1. Clone this repository.
1. Install [Vale][1] with `brew install vale` (macOS) or `choco install vale` (Windows).
1. Download the Google Vale rules:
  - open a shell and change directory into this repo
  - run the command `vale --config ./vale.ini sync`

## Configure VS Code

1. Add the [Vale extension][2]
1. Open VS Code Settings (⌘,)
1. Search for **Vale CLI** and in **Vale CLI: Config** specify the path to the Vale config file included in this repo. For example:
    ```bash
    /Users/<you>/GitHub/starrocks-vale/vale.ini
    ```
Once you have VS Code configured and restarted you should see squiggles under potential issues in Markdown files. Here is an example:

![VS Code linting][5]

The same information is presented in GitHub when doc PRs are submitted, as a GitHub workflow will add reviews:

![GitHub review][6]

## Change the rules

Vale will report issues that we disagree with. When this happens change the rules. There are two (at least two) ways to do this:
- Add to our custom vocabulary file
- Turn a rule off

See [Contributing][7]

## GitHub workflow

A working example workflow, [`linting.yml`][3] is provided. Once this workflow is in production use it would probably be best to copy the content from the `StarRocks/StarRocks` repo.

## License

Code—including sample code—in this repository is licensed under the [Apache 2.0 license][4].


[1]: https://vale.sh/
[2]: https://marketplace.visualstudio.com/items?itemName=ChrisChinchilla.vale-vscode
[3]: ./examples/linting.yml
[4]: https://github.com/StarRocks/starrocks/blob/main/LICENSE.txt
[5]: ./examples/vs-code-linting.png
[6]: ./examples/github-actions-linting.png
[7]: ./CONTRIBUTING.md