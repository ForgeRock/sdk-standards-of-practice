# Git Workflow Suggestions and Tips

## Getting started

1. Make sure you have Git on your local computer, version 2.39 or higher
2. Make sure you have a usable Github account
3. Follow the [guide here to create your GPG keys for signing your commits](https://docs.github.com/en/authentication/managing-commit-signature-verification)
4. If you want to use SSH for cloning, pulling and pushing, [create your SSH keys with this guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)

## The Basics

1. Read the first three chapters from [Git SCM book](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
2. Skip to [chapter six from the same book](https://git-scm.com/book/en/v2/GitHub-Account-Setup-and-Configuration)
3. Review the PDF from presentation: [WTF is Git(hub)?](https://www.dropbox.com/scl/fi/k8bjmdne9tvcjquny549g/WTF-is-Git-hub.pdf?rlkey=zahvqoniznsrrd6kn45av4g3r&dl=0)

## Terminology

1. `upstream`: the official, organizational repo; e.g. github.com/ForgeRock/javascript-sdk
2. `origin`: your personal "fork" of the `upstream`; e.g. github.com/janedoe/javascript-sdk
3. `main`: this is our "release" branch, used to be called `master`, that represents the released state of code †
4. `develop`: this is the main "development" branch that reflects the pre-release state of code ††
4. *feature branch*: this is a temporary branch that contains changes intended to be merged into `develop`
5. rewriting history: commits in Git are line items in a ledger of sorts (think blockchain'ish), rewriting history is altering these items and their resulting SHAs
6. `rebase`: a Git command that allows you to rewrite history

† There's often more complexity with branching for some projects (typically applications), though we don't use them:

1. `stage`: potential release candidate
2. `prod`: production release, can also be called `release`

†† This isn't always called `develop`, it can also be called `beta` or `canary`, but the intention remains the same

## Workflow

We use a unidirectional, rebase flow for version management. This means you pull changes from the `develop` branch (or `beta`, depending on the project) on `upstream`, which is the official, organizational repo, and you push changes to a feature branch located on either `origin` (this is a good place to push incomplete code), which is your own fork of the repo, or the official `upstream` (good for near complete or complete code).

For more information regarding this workflow, see [this slide printout about Git(hub) Workflow](https://www.dropbox.com/scl/fi/ey4iyb5it9ersmrg5mmv2/Git-hub-Workflow.pdf?rlkey=l4nsxptu229h60wrzu1fgul5g&dl=0).

## Commits

In general, commits should be meaningful, logically separated from other commits, and clear to read in the log. We follow the industry standard, [Conventional Commit specification](https://www.conventionalcommits.org/). In addition, we recommend writing your Jira ticket number in the PR title, at the end.

For example:

```txt
feat(token-vault): add transaction tracing for better analytics; SDKS-9999
```

The above translates to a "feature" being added to the sub-project "Token Vault" to enable better analytics, tracked in Jira ticket SDKS-9999.

A good habit to adopt is to commit early, and commit often. To reduce commit clutter, use `git commit --amend` once you've written your first commit. The `--amend` flag just adds your changes to your previous commit. Add a separate commit only if the changes you've just introduced are meaningful, and logically separate from your previous commit.

WARNING: don't use `--amend` if you haven't already written your first commit.

Keeping your commits to a minimum is very advantageous when you need to do a rebase. More commits mean more conflicts to resolve to complete a rebase.

### Rules

Rules found within the Conventional Commit specification

## Rewriting History (Rebasing)

Rebasing allows you to rewrite the commit history of your project. It's powerful and therefore comes with some rules and needed skill. But, the end result is a cleaner and easier to read Git log.

For more [information on how rewriting works, please read this article](https://cerebralideas.com/blog/rewriting-git-history) (aka why does it say my commit history is not up to date after rebasing or ammending?).

### Rules

1. Never rewrite someone else's history
2. Never rewrite public history
3. Keep new commits to a minimum (3 or less)

## Pull Requests

Pull requests are best treated as a conversation about code. This means the individual creating the PR needs to initiate the conversation by providing context through an explanatory description including sceenshots, animated GIFs, if applicable. Not doing this is essentially handing someone something, and then just walking away.

Review PDF from presentation: [How to PR](https://www.dropbox.com/scl/fi/hbno7ulqjz7ot2tszg4ac/How-to-PR.pdf?rlkey=8wgnx29dkpq04jlu1ybizj92f&dl=0).

### Rules

1. PRs should have a good description providing context for the reviewer
2. PRs should have 1 to 3 commits, each commit must be meaningful and logically separated from the others
3. PRs should have Github comments on the portions of code changes that are points of focus for the reviewer
4. PRs should have minimum code changes within files unrelated to the feature or bug fix

## Reviewing PRs

Reviwing someone's PR should be the continuation of the conversation started by the PR creator. Read through the description, and attached images or GIFs to familiarize yourself with the changes. Then, review the code related comments left by the creator to help focus or guide your attention.

When ready, start leaving comments as "review comments". That way they get bundled up into a single thread. Comments should be meaningful and encourage clarity and throughtful discussion. They should be focused on the code and not the person.

### Rules

1. Comments should focus on the code and NOT the author
2. Comments should focus on readability and "understandability"
3. Comments should focus on design patterns and idiomatic conventions
4. Comments should not focus on nits (ESLint/Prettier should remove before PR creation)
5. Comments should assume author has more context and has arrived at code with reason

### Reading list

- [How to Make Good Code Reviews Better - Stack Overflow Blog](https://stackoverflow.blog/2019/09/30/how-to-make-good-code-reviews-better/)
- [Code Review Developer Guide | eng-practices](https://google.github.io/eng-practices/review/)
- [Code Review Guidelines for Humans](https://phauer.com/2018/code-review-guidelines/)
- [The 7 Code Review Manners](https://reutsharabani.medium.com/the-7-code-review-manners-f0f0eef4d3e5)

## Semantic Versioning

This is directly related to Git(hub), but it is definitely related to how we publically version our libraries, frameworks and SDKs. We roughly follow the Semantic Versioning spec, also known as Semver. You can [read more about it from this resource](https://semver.org/).
