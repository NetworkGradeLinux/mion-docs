# Git Commandments

![Yey git](https://imgs.xkcd.com/comics/git.png  "git")

**Git Workflow**

For those new to git threre are a number of good guides provided by GitHub available [here](https://guides.github.com/)

We follow the standard [GitHub Workflow](https://guides.github.com/introduction/flow/)
- This applies to all of the main repos: mion, meta-mion, meta-mion-stordis, etc.
- Changes must be made on a private branch named <username/brief_description_of_change>
    * Please create a branch rather than a fork. A fork would be for a sibling project, that does not merge back into the default branch of the main project.
- A pull request is created and the maintainers of the repo are added as reviewers
- After the change is merged, the branch is deleted (this should be done during the merge)

**GitHub Permissions**

GitHub Teams are used to manage permissions to repos:

- Mion Dev - grants write permission to the main Mion development repos

**Git Commit Messages** 

[General guidelines](https://chris.beams.io/posts/git-commit/#seven-rules) for writing good Git commits, the TL;DR is:
- Subject line summarises the commit and is written in the imperative "Fix compile issue on X architecture"
- Subject line limited to 50 chars, capitalised with no full stop
- Body wrapped to 72 chars and explains what and why (not how)
- Body references bugs/issues in GitHub

In order to maintain the standards setup by the OpenEmbedded and Yocto Projects, we ask developers to utilize the same git commit standards used by these projects.

[These standards](http://www.openembedded.org/wiki/Commit_Patch_Message_Guidelines), are outlined here.

Please read and adhere to these standards.

**Git Branching strategy**

seriously, lets not make it any more complicated than it needs to be.. 

Our branches track the Yocto Project branches. Master tracks master in openembedded-core, Dunfell, dunfell, etc. Main development is being done on Dunfell for now, if additional resources are there we can start tracking master.
