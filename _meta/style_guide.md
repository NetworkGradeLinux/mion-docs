# mion Writing Style Guide
This style guide is to provide some general guidelines for written 
communications. It is being kept simple so as to allow individual voices to be 
heard and in doing so form the collective voice of mion.

## Spelling, Grammar, and Word Choice

* In general US spelling of words, especially of technical terms, should be
  used.

* For date and time, use the International Organization for Standardization's 
  (ISO) 8601 format: YYYY-MM-DD. See
  [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) for more
  information.
  
Try to avoid often used corporate buzzwords and phrases outside of their 
original meaning:

    * Disruptive 
    * Synergy
    * Closing the loop
    * Wheelhouse
    * +1
    * Leverage
    * Vertical
    * Paradigm shift

These words tend to lose their meaning over time, and can be viewed negatively
by some. You may use them, but do so with consideration.

> This can also apply to tech jargon. While both buzzwords and jargon can aid in 
  communication, be mindful of your audience. 

For all documents, be concise. Consider the following suggestion:
**Delete all you can while retaining the statement's meaning and also avoiding 
ambiguity and vagueness.**

## Inclusivity and Supporting Diversity
Some language can have negative, hurtful, or otherwise 
biased/discriminatory meanings or uses that should be avoided.

This section is not comprehensive, and is used to illustrate language which
can be offensive, reinforce bias, or otherwise create exclusion, and may be used
in a technical setting. In the future, there may be a "linter" for the style 
guide: detection of biased-language will be flagged by the linter, but it is 
still the responsibility of the writer to review documents.

### Gender
In generic circumstances, gender-neutral terms should be chosen. Rather than
"he" or "she", try to use alternatives such as using the second person "you",
or "they" for a generic single person. When referencing or quoting a 
specific person use the pronouns they use.

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
  that has not yet been updated. Consider making a note stating such if this 
  is the case, however.

### Accessibility 
* Use the following web development tools to check for contrast and other
  design elements which may effect readability or hinder a screen reader:
  - [Google Chrome's Lighthouse](https://developers.google.com/~/lighthouse)
  - [WAVE](https://wave.webaim.org/)
  - [tota11y](https://khan.github.io/tota11y/) 
* For images provide alternative text or use 
  descriptive names for the files.

## Miscellanea
**Font**: When font choice is an option, please choose an open source font. 
      Monospace fonts, such as [FiraCode](https://github.com/tonsky/FiraCode)
      would be a good choice.

**Format**: For technical documentation, use 
[github](https://github.github.com/gfm/) flavored markdown.

**Capitalization**: 'mion' should always be lowercase.

**Column length**: 
* **Markdown**: Column length must be done so that line breaks are rendered correctly: Two spaces after a line will cause a linebreak, which can accidently be entered when trying to keep lines under a certain length. It is often easier to not adhere to a set length.
* **Git** commit messages, the maximum length is 72.

-------------------------------------------------------------------------------
