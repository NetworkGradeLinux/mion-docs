# Contributing

Welcome to mion-docs! Here you can find info on how to contribute to mion-docs.
If you want to contribute to another part of the project, please see the general
contributing documentation
[here](https://github.com/NetworkGradeLinux/mion/blob/dunfell/CONTRIBUTING.md).

## Table of Contents

[Before You begin](#before-you-begin)

[Setup](#setup)

[Making Changes](#making-changes-to-documentation)

[Maintainer Contact](#maintainer-contact)

## Before You Begin

* Please read our [Code of Conduct](docs/community/code-of-conduct.md)
and our [interpretation](docs/community/Coc-interpretation). By contributing to
the project, you agree that you've read and will follow the Code of Conduct.

* The documentation is written using Markdown; see <https://www.markdownguide.org/>
for reference.

* Read and become familiar with our [git workflow](_meta/git_commandments.md),
though an overview is provided below.

* All documentation is expected to follow the [mion style guide](_meta/style_guide.md).

Lastly, find or report an issue [here](https://github.com/NetworkGradeLinux/mion-docs/issues).
For existing issues, add a comment that you'd like the issue assigned to you.
You can also open an issue, if you've been added to the docs team.
If you're not part of the team, let a maintainer know, and we can help add you.

> Look for ones labeled `good first issue` if you haven't contributed yet.

## Setup

This section assumes that you are at least a little familiar with git and
using a command line interface on a Linux distro or macOS. However, you can
still contribute if you're not; if you need help with other environments, or
using any tools, get in touch with [us](#maintainer-contact) and we can
offer assistance.

In any of the following examples the command line/terminal, lines that start
with `#` are comments, so don't worry about them if you want to copy/paste.

If you don't already have an account on github, go to <https://github.com/join>

### Authentication

You need to tell github that you're you!
If you haven't verified your email with github, you will need to do so.
See <https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/verifying-your-email-address>
for how to do so.

Configuring git with your name and the email account used on github
Open a terminal:

> `ctrl+alt+T` with Ubuntu, or just do an application search for "term"

```shell
# If you don't want to use the same name and email for all git projects, leave
# out --global, and enter the information after you've cloned the mion-docs
# repo and entered the  directory

git config --global user.name "First Last"

git config --global user.email "your@email.com"

```

Now make sure that your GitHub account has
[two-factor auth](https://GitHub.blog/2013-09-03-two-factor-authentication/)
This help secure your account and ensure that it's you submitting changes.
For all things related to
authentication, see
<https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github>.

### Getting the source

If you have ssh enabled in github:
`git clone git@github.com:NetworkGradeLinux/mion-docs.git`

Otherwise:
`git clone https://github.com/NetworkGradeLinux/mion-docs.git`

All the documentation files will now be in the folder `mion-docs`.

## Making Changes to Documentation

If you're not familiar with a command line text editor such as vim, emacs, or
nano, you can use one with a graphic interface. These include
gedit(if you use a gnome based desktop such as Ubuntu), kate(KDE desktop)
TextEdit, and notepad, and you likely already have one installed by default.

Before making any changes, create a new branch with your github username
followed by a slash(/) then a bit describing what you're changing in just a few
words separated by a dash(-) and no spaces. For example, "fix-readme-typo",
"glossary-updates". You'll get to explain in more detail when it comes time to
commit. This format helps keep track of changes and allows maintainers have a
quick idea of what is being submitted and by whom.

In a terminal:

```shell
# change into the mion-docs directory
cd mion-docs

# replace "userName" with your github name and "what-you-are-changing" with
# just that

git checkout -b userName/what-you-are-changing
```

You can now get to work!

### Working On Main Documentation

For anything that's in `mion-docs/docs/`, or changes `_config.yml`, you need
to test using jekyll. If you don't have Jekyll installed,
checkout these [instructions](https://jekyllrb.com/docs/installation/) for help.
Once jekyll is installed, change to the top-level directory(`mion-docs`) on
the command line, and run `bundle exec jekyll serve`. In your web browser,
navigate to <http://localhost:4000> to see the changes.

### Changes to Meta Documentation

If you're working on this README or anything in either `_meta` or in the
_drafts folder, `_drafts`, you can easily view how the markdown will look
using [grip](https://github.com/joeyespo/grip). See link for installation and
use.

## Submitting Changes

Done making changes? Everything looks good? Then it's time to add your file and
commit.

In a terminal:

```shell
# add the file you changed or added, such as docs/about.md
git add path/filename

# commit time!

git commit --signoff
```

> This will start the default editor defined in your git config. To change, run
`git config --global core.editor name_of_editor`

If you need help with the commit message, refer back to
[git workflow](_meta/git_commandments.md) or ask another member of the docs
team.

**If you made multiple commits on your branch** before finishing up and putting
in a pull request, be sure to rebase and squash/fixup so that you're submitting
only one change to be merged into the main branch:
[github git rebase tutorial](https://docs.github.com/en/free-pro-team@latest/github/using-git/using-git-rebase-on-the-command-line#pushing-rebased-code-to-github)
> Git rebase can take a bit to get the hang of! Please don't hesitate to ask for
help!

Almost done! Now it's time to push your branch onto github:
`git push -u origin username/what-you-are-changing`

Lastly, go to <https://github.com/NetworkGradeLinux/mion-docs> and submit a pull
request for your branch to be merged with dunfell. We will let you know if
there're any issues and what corrections need to be made. After your pull
request is merged, delete your branch from the remote repo. (Though you can keep
it on your computer if you want to)

## Maintainer Contact

If you have questions, feel free to ask us in our
[Slack channel](https://networkgradelinux.slack.com) or email Maintainer Kat
at igorina@toganlabs.com
