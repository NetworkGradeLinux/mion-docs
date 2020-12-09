# mion Writing And Communication Style Guide

This style guide is to provide some general guidelines for written
communications. It is being kept simple to allow individual voices to be
heard and in doing so form the collective voice of mion.

When working in markdown, check syntax and style issues by using
[markdownlint](https://github.com/markdownlint/markdownlint).

## Spelling, Grammar, and Word Choice

* In general US spelling of words, especially of technical terms, should be
  used.

* For date and time, use the International Organization for Standardization's
  (ISO) 8601 format: YYYY-MM-DD. See
  [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) for more
  information.

Try to avoid often used corporate buzzwords and phrases outside their
original meaning:

    * Disruptive 
    * Synergy
    * Closing the loop
    * Wheelhouse
    * +1
    * Leverage
    * Vertical
    * Paradigm shift
    * Pivot

These words tend to lose their meaning over time, and can be viewed negatively
by some. You may use them, but do so with consideration.

> This can also apply to tech jargon. While both buzzwords and jargon can aid in
  communication, be mindful of your audience.

For all documents, be concise. Consider the following suggestion:
**Delete all you can while retaining the statement's meaning and also avoiding
ambiguity and vagueness.**

## Inclusivity and Supporting Diversity

Some language can have negative, hurtful, or otherwise biased/discriminatory
meanings or uses that should be avoided.

This section is not comprehensive, and is used to illustrate language which
can be offensive, reinforce bias, or otherwise create exclusion, and may be used
in a technical setting. In the future, there may be a "linter" for the style
guide: detection of biased-language will be flagged by the linter, but it is
still the responsibility of the writer to review documents.

### Gender

In generic circumstances, gender-neutral terms should be chosen. Rather than
"he" or "she", try to use alternatives such as using the second person "you",
or "they" for a generic single person. When referencing or quoting a specific
person use the pronouns they use.

| Rather than...                                          | Consider...                                       |
|---------------------------------------------------------|---------------------------------------------------|
| When a programmer is stuck, *he* should talk to a duck. | When **you** get stuck, talk to a duck.           |
| *He/she* can be a great listener.                       | **They** can be a great listener.                 |
| Ms. Ducky has given me many hours of *their* time       | Ms. Ducky has given me many hours of **her** time |

### Race and Ethnicity

Some language to watch out for and alternatives:

| Don't use...        | Consider...                               |
|---------------------|-------------------------------------------|
| Master/slave        | main/second, Primary/replica, Boss/Minion |
| hang                | stops, freezes, doesn't respond           |
| Blacklist/whitelist | blocklist/allowlist                       |

> Keep in mind that it's permissible to use the outdated technical terms if
  they exist within code being referenced, or a primary source of information
  that has not yet been updated.Please make a note stating such if this is the
  case, however.

### Accessibility

* Use the following web development tools to check for design elements which
effect readability or hinder a screen reader:

  * [Google Chrome's Lighthouse](https://developers.google.com/~/lighthouse)
  * [WAVE](https://wave.webaim.org/)
  * [tota11y](https://khan.github.io/tota11y/)

* For images provide alternative text or use descriptive names for the files.

## Miscellanea

**Font**: When font choice is an option, please choose an open source font.
Monospace fonts, such as [FiraCode](https://github.com/tonsky/FiraCode) would
be a good choice.

**Format**: For technical documentation, use
[github](https://github.github.com/gfm/) flavored markdown.

**Capitalization**: 'mion' should always be lowercase.

**Markdown Column Length**: The most important point is that markdown is
rendered properly. If using a specific column length, make sure to check that
there is no white-space between lines. Be aware that two white-spaces create a
line break in markdown. When using [markdownlint](https://github.com/markdownlint/markdownlint)
to check for syntax and style issues, it flags lines that go past column 80,
with the exception being lines that can't be broken up,such as links. As such,
column 80 is acceptable given that you check that there isn't any unintended
newlines.

**Companies and Projects:** When referring to a company,project, or product,
check that capitalization and name are correct. If there has been a change in
a name, update and reflect that. For example, when talking about what had been
"the STORDIS BF2556X-1T", it should now be referred to as "the APS Networks
(formerly STORDIS) BF2556X-1T". When porting a new switch over, it is a good
idea to check that the information around it is up to date when writing
documentation.

**Links:** When providing links, use the word that you want to bring attention
to. In other words, no [click here]( https://www.w3.org/QA/Tips/noClickHere).

-------------------------------------------------------------------------------
