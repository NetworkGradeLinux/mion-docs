# mion-docs

## Welcome to the mion-docs repository

**Looking for NGL/mion documentation?**
[https://mion.docs.io](https://docs.mion.io).

For viewing directly from GitHub, see the quick links below.

Keep reading if you want to contribute to the docs.

## Documentation Links

* [About](docs/about.md)

* [Accessibility](docs/ACCESSIBILITY.md)

* [Getting Started](docs/getting-started.md)

* [Git workflow](_meta/git_commandments.md)

* [Glossary](docs/glossary.md)

* [I^2C Issues](docs/i2c-issues.md)

* [Image Types](docs/imagetypes.md)

* [Installing mion](docs/installing_mion.md)

* [Resources](docs/resources.md)

* [Style Guide](_meta/style_guide.md)

## Structure/Directory layout

General Documentation can be found under `docs/`, except for `index.md`, which
is in the top directory.

Also in the top directory is this README and the license file.

Within `_meta/` you can find the documentation style guide, mion-docs
meeting minutes, our git workflow, and other materials related to both mion-docs
and general project guidelines that may be helpful info for contributors.

## Contributing

Want to contribute? Find an existing issue not assigned to anyone
[here](https://github.com/NetworkGradeLinux/mion-docs/issues) and add a comment
that you'd like to work on that issue. You can also open an issue if you've
been added to the docs team. If you're not part of the team, just let a
maintainer know, and we can help add you.
> Look for ones labeled `good first issue` if you haven't contributed yet.

The documentation is written using Markdown. If you're not familiar or need a
reference, checkout <https://www.markdownguide.org/>.

Read and become familiar with our [git workflow](_meta/git_commandments.md) and
The [mion style guide](_meta/style_guide.md), though an overview will be
provided below.

### Getting Ready

This section assumes that you are at least a little familiar with git and
using a command line interface on a Linux distro or macOS. However, you can
still contribute if you're not; if you need help with other environments, or
using any tools, get in touch with [us](#maintainer-contact) and we can
offer assistance.

In any of the following examples the command line/terminal, lines that start
with `#` are comments, so don't worry about them if you want to copy/paste.

If you don't already have an account on github, go to <https://github.com/join>

#### Authentication

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
# repo and entered it's directory

git config --global user.name "First Last"

git config --global user.email "your@email.com"

```

Now make sure that your GitHub account has
[two factor auth](https://GitHub.blog/2013-09-03-two-factor-authentication/)
This help secure your account and ensure that it's you submitting changes.
For all things related to
Authentication, see
<https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github>.

#### Getting the source

If you have ssh enabled in github:
`git clone git@github.com:NetworkGradeLinux/mion-docs.git`

Otherwise:
`git clone https://github.com/NetworkGradeLinux/mion-docs.git`

All the documentation files will now be in the folder `mion-docs`.

### Making Changes to Documentation

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

#### Working On Main Documentation

For anything that's in `mion-docs/docs/`, or changes `_config.yml`, you need
to test using jekyll. If you don't have Jekyll installed,
checkout these [instructions](https://jekyllrb.com/docs/installation/) for help.
Once jekyll is installed, change to the top-level directory(`mion-docs`) on
the command line, and run `bundle exec jekyll serve`. In your web browser,
navigate to <http://localhost:4000> to see the changes.

#### Changes to Meta Documentation

If you're working on this README or anything in either `_meta` or in the
_drafts folder, `_drafts`, you can easily view how the markdown will look
using [grip](https://github.com/joeyespo/grip). See link for installation and
use.

### Submitting Changes

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

### Maintainer Contact

If you have questions, feel free to ask us in our
[Slack channel](https://networkgradelinux.slack.com) or email Maintainer Kat
at igorina@toganlabs.com
