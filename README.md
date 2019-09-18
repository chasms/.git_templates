# .git_templates

This repository is designed to provide a means for setting up global git hooks via hook templates.

## Setup

1. Clone this repository directly into your home directory:
    ```
    cd ~
    git clone git@github.com:chasms/.git_templates.git
    ```
1. Set this repo up as your git template directory:
    ```
    git config --global init.templatedir '~/.git_templates'
    ```
1. Install the `git` gem to enable scripting:
    ```
    gem install git
    ```

## Usage

The hooks in this repository will automatically be installed in any newly initialized or newly cloned git repos.

To use them with an existing repository, run `git init` in that repository to reinitialize with the templated hooks.

In all cases, templated hooks **will not overwrite** existing hooks, either pre-existing or previously installed via these templates. This means that if you want to make changes to any hook template and want to see those changes carry over to that hook in a repository, you will need to delete the current hook in that repository's `.git` directory and then re-run `git init`.

## Hooks

| Name | Function |
|-|-|
| `post-commit` | This hook writes all commits to a `commit_log.txt` file located in your home directory. Formatting for commit logs is as follows: `Wed, Sep 18 2019 01:48pm [repository:branch] commit message` |

## Bonus

Add this function to your `.bashrc` or `.bash_profile` to make pulling up and searching commits as easy as typing `commits` into your terminal:

```
commits () {
  cat ~/commit_log.txt | grep $@
}
```
