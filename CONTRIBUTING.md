# Contributing

Welcome to mion-docs! Here you can find info on how to contribute to mion-docs.
If you want to contribute to another part of the project, please see the general
[contributing documentation](https://github.com/NetworkGradeLinux/mion/blob/dunfell/CONTRIBUTING.md).

Previously, contributing to mion-docs required following a workflow very similar
to the other repositories. This approach is still encouraged, especially if
you're new to our workflow or contributing to open source. However, if you need
to just submit a change and are already set up on GitHub, submit a pull
request from a branch or fork, or send the docs-maintainer a patch when you're
done, and once approved, the gh-pages branch will be updated by the maintainer.

Want to know how to preview changes to `docs.mion.io` on your computer? Or how
to get started with git?  What if you're new to our community and want to get
a good grasp on what are workflow is like? Read on!

> mion-docs also has a [wiki](https://github.com/NetworkGradeLinux/mion-docs/wiki),
which is used for developer documentation, such as testing procedures, meeting
minutes, and other information that relates to the development of mion. The wiki
does not require the same setup of the rest of the documentation, and can be
edited directly from GitHub. That said, please let other developers know if you
are editing a page to avoid overlap/merge conflicts. Please write pages in
Markdown. If you chose to edit it locally, like the doc maintainer, take extra
care, and note that the wiki does not have multiple branches.

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

* Read and become familiar with our [git workflow](https://github.com/NetworkGradeLinux/mion-docs/wiki/git_commandments),
though an overview is provided below.

* All documentation is expected to follow the [mion style guide](https://github.com/NetworkGradeLinux/mion-docs/wiki/style_guide).

You can find or report an issue at [mion-docs](https://github.com/NetworkGradeLinux/mion-docs/issues).
For existing issues, add a comment that you'd like the issue assigned to you, or
attend the [fortnightly bug-scrub](https://docs.mion.io/latest/community/Community/)
listed on our community about page.

> Look for ones labeled `good first issue` if you haven't contributed yet. These
tend to be easier bugs for newcomers to work on.

## Setup

This section assumes that you are at least a little familiar with git and
using a command line interface on a Linux distro or macOS. However, you can
still contribute if you're not; if you need help with other environments, or
using any tools, get in touch with [us](#maintainer-contact) and we can
offer assistance.

In any of the following examples the command line/terminal, lines that start
with `#` are comments, so don't worry about them if you want to copy/paste.

If you don't already have an account on GitHub, go to <https://github.com/join>

### Authentication

You need to tell GitHub that you're you!
If you haven't verified your email, you will need to do so.
See <https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/verifying-your-email-address>
for how to do so.

Configuring git with your name and the email account used on GitHub
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

If you have ssh enabled:
`git clone git@github.com:NetworkGradeLinux/mion-docs.git`

Otherwise:
`git clone https://github.com/NetworkGradeLinux/mion-docs.git`

All the documentation files will now be in the folder `mion-docs/docs`.

## Making Changes to Documentation

If you're not familiar with a command line text editor such as vim, emacs, or
nano, you can use one with a graphic interface. These include
gedit(if you use a gnome based desktop such as Ubuntu), kate(KDE desktop)
TextEdit, and notepad, and you likely already have one installed by default.

Before making any changes, create a new branch with your GitHub username
followed by a slash(/) then a bit describing what you're changing in just a few
words separated by a dash(-) and no spaces. For example, "fix-readme-typo" or
"glossary-updates". You'll get to explain in more detail when it comes time to
commit. This format helps keep track of changes and allows maintainers have a
quick idea of what is being submitted and by whom.

In a terminal:

```shell
# change into the mion-docs directory
cd mion-docs

# replace "userName" with your GitHub username and "what-you-are-changing" with
# just that

git checkout -b userName/what-you-are-changing
```

You can now get to work!

We use [MkDocs](https://www.mkdocs.org/) with the
[MkDocs-material theme](https://github.com/squidfunk/mkdocs-material) and
the [mike versioning utility](https://github.com/jimporter/mike) to generate and
publish our documentation. In most cases you will not need to check versioning,
and can ignore `mike`. To install `MkDocs` and the theme, all you have to do is
install the theme using Python's `pip`. On the command line:
`pip install mkdocs-material`. This will also install all the dependencies. You
may have to install pip, which can be installed using the package manager
available to you. Feel free to ask a maintainer if you need help.

As you make changes, run `mkdocs serve` on the command line. In a browser,
navigate to <http://127.0.0.1:8000> to see your changes and to ensure everything
looks correct when rendered into html. If making
changes to formatting, make sure to [check accessibility](https://docs.mion.io/latest/ACCESSIBILITY/).

## Submitting Changes

Done making changes? Everything looks good? Then it's time to add your file and
commit.

> Important: Never push to the `gh-pages`. This is to be done by a maintainer
once your changes are approved.

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
[git workflow](https://github.com/NetworkGradeLinux/mion-docs/wiki/git_commandments)
or ask another member of the docs team.

Almost done! Now it's time to push your branch onto GitHub:
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
