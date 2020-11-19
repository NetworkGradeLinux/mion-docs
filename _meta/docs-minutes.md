# mion-docs Meeting Minutes

## Meeting 1, 2020-11-05

### Documentation process

* Follow the same process as for merging code into the other github mion repos
* as it is described in here: <https://github.com/NetworkGradeLinux/mion-docs/blob/dunfell/_meta/git_commandments.md>
* Commit messages
* New features should be documented by the person writing the code.
* Docs should be tested on locally with Jekyll - depending on the change
  * Kat to document this as part of the process
  * Should be replaced by an integration docs site (Kat to explore)
  * Linter for markdown on pull requests -
    * 100 column width maybe?
* Community contributions - Frédéric to do a test submission for review

### TODO

* Elect maintainers - Kat and Mike
* Enforce restriction on merging own code - for all repos (Mike/John to do this)
* Pull request template for the code (Mike to show John how to do this)
* Prerequisite knowledge document in the mion docs (Mike - John to send on the
  starting doc)
* Book a recurring meeting for documentation - every second week?
* Figure out the difference between the source and binary distribution - some
* users will need a fast getting start guide based on binary installer (Kat?)

-------------------------------------------------------------------------------

## Meeting 2, 2020-11-19

* Code of Conduct was brought up, will be moving from `_drafts/` to `docs/`, after
  being reviewed by project team leader Ben.

* Katrina brought up the use of the `_drafts/` folder as a semi-informal staging
  area.

* John documented using lab equipment in aps-docs and is working on adding a
  porting.md for meta-mion-bsp, which will be sent to the docs team for review
  early next week. This is a **high priority** task, as it's importance is
  second only to the getting started guide. When finished it must be added to
  the main docs page.
  
* Katrina is working on finishing the contributing document for the `mion` repo,
  which needs to get done very soon due to the increase in interest of the
  project.
  
* Ben raised the importance of the front page/intro content. Katrina to comment
  on existing issue or raise a new one, adding what needs to be stated, so that
  people can actually know what the project is about, an important point which
  many open source projects forget to prioritize.
  
* John made an important point that Prior to 0.9.1, All documents must be
  reviewed as part of the release process. Once a release is made, documentation
  can't be modified. Related to this is the need to archive docs for a release.
  The docs repo is to use release version tags as well, such as done by the
  Yocto Project.

* As part of the release process, docs team must flag the engineering team, to
  make sure that all documentation is up to date. Release process will be added
  to `_meta/`. The current release process can be found in the `meta-ci` repo.

* Mike is to help figure out a script or program using the github api that will
  provide the docs team a list of merges to dunfell/main branches of the other
  mion repos on a weekly basis so that docs team can work in tandem with the
  engineers, documenting as changes are made. In the mean time Katrina will
  manually check for this.

* Mike pointed out that the use of `_drafts/` and how it relates to branches
  should be figured out, to keep things clean and orderly.
  
* The Docs team is to attend the weekly bug scrub meeting, which will also be
  open to the public community.
