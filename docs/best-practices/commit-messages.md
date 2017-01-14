# Git Commit Messages for CiviCRM

# Background

Commit messages appear in many contexts -- e.g. in "git log", "gitk",
"github", Jenkin's test runs, email notifications, and JIRA's "Commits"
tab. To ensure that a commit message is easy to read in all contexts, it
should generally:

-   Start with a meaningful one-line summary.
-   Include a reference to a JIRA issue.\

Of course, writing a good commit message takes a little time, and some
folks don't want to spend the time. Shame on you! But... laziness is a
powerful force, and we're not going to persuade everyone to spend time
writing beautiful messages. Fortunately, CiviCRM includes some [git
hooks](http://git-scm.com/book/en/Customizing-Git-Git-Hooks) (like
[git-footnote](https://github.com/totten/git-footnote)) which can
automatically enrich your commit message:\

-   Any time you reference a JIRA issue in any part of a commit message,
    git-footnote will look up the issue and append a hyperlink to the
    commit message.
-   If you write a 1-2 word commit message ("CRM-1234" or "fix
    CRM-1234"), git-footnote will put the JIRA title in the summary
    line.\

# Examples

When writing commit messages, these are some examples of good/bad
patterns to consider. (Note: The first line is displayed in bold because
it's often the only line displayed when browsing through commits.)\



Your Commit Message

Final Commit Message (after running git-footnote)

Awesome

**CRM-1234 - Subsystem - Summarize what the commit does**

Also write a longer explanation of what the commit does. You don't need
to give a detailed lesson on how everything works, but it may help to
describe the corner-case or obscure interaction you were thinking about,
or it may help to reference other relevant issues (like CRM-4567 or
CRM-8901). Add whatever seems useful.

**CRM-1234 - Subsystem - **Summarize** what the commit does**

Also write a longer explanation of what the commit does. You don't need
to give a detailed lesson on how everything works, but it may help to
describe the corner-case or obscure interaction you were thinking about,
or it may help to reference other relevant issues (like CRM-4567 or
CRM-8901). Add whatever seems useful.

---\
  \* CRM-1234: The Issue Title From JIRA\

[http://issues.civicrm.org/jira/browse/CRM-1234](http://issues.civicrm.org/jira/browse/CRM-1234)\
  \* CRM-4567: The Other Issue Title From JIRA\

[http://issues.civicrm.org/jira/browse/CRM-4567](http://issues.civicrm.org/jira/browse/CRM-4567)\
  \* CRM-8901: The Third Issue Title From JIRA\

[http://issues.civicrm.org/jira/browse/CRM-8901](http://issues.civicrm.org/jira/browse/CRM-8901)

Great

**CRM-1234 - Subsystem - **Summarize** what the commit does**

**CRM-1234 - Subsystem - **Summarize** what the commit does**

---

 \* CRM-1234: The Issue Title From JIRA\

[http://issues.civicrm.org/jira/browse/CRM-1234](http://issues.civicrm.org/jira/browse/CRM-1234)

Good

**CRM-1234 - **Summarize** what the commit does**

**CRM-1234 - **Summarize** what the commit does**

---

 \* CRM-1234: The Issue Title From JIRA\

[http://issues.civicrm.org/jira/browse/CRM-1234](http://issues.civicrm.org/jira/browse/CRM-1234)

OK

**CRM-1234**

**CRM-1234 - The Issue Title From JIRA\
**

[http://issues.civicrm.org/jira/browse/CRM-1234](http://issues.civicrm.org/jira/browse/CRM-1234)

OK

**fix CRM-1234**

**fix CRM-1234 - The Issue Title From JIRA**

[http://issues.civicrm.org/jira/browse/CRM-1234](http://issues.civicrm.org/jira/browse/CRM-1234) **\
**

OK

**Subsystem - **Summarize** what the commit does**

**Subsystem - Summarize what the commit does**

So-So

****Summarize** what the commit does**

******Summarize**** what the commit does**

Terrible

**cleanup**

**cleanup**

\

# Hook Installation

To take advantage of the automatic formatting on commit messages, you
must enable CiviCRM's [git
hooks](http://git-scm.com/book/en/Customizing-Git-Git-Hooks). The
"gitify" tool (discussed in [Contributing to CiviCRM using
GitHub](/confluence/display/CRMDOC/Contributing+to+CiviCRM+using+GitHub))
will create the hooks if you include the "--hooks" option. If you didn't
originally use "gitify" with the "–hooks" option, then just re-run
"gitify" and add the "--hooks" option this time. ("gitify" won't replace
your existing git repos, but it will register hooks on them.)\

If you cannot or do not want to use "gitify", then you can [review the
standard git hooks included with
CiviCRM](https://github.com/civicrm/civicrm-core/tree/master/tools/scripts/git)
and write your own. Be sure to look at each of your git repositories
("civicrm-core", "civicrm-drupal", etc) to ensure the hooks are
registered.\

# FAQ

-   **Q: What if I write something that doesn't have a JIRA issue?**
-   A: It's generally good practice to create a JIRA issue before
    working on a problem, then reference the issue in the commit
    message. However, if that seems inappropriate, then make reference
    to the general **area or subsystem** instead.
-   **Q: What is an "area" or "subsystem"?**\

-   The term is purposefully ambiguous - it's difficult to think of a
    hard rule, and it seems to depend on how many lines/files/functions
    were touched. It might be the name of a class, a function, a
    template, a directory, or a component. The goal is the provide some
    clue to the future reader so that she can guess which commits would
    be relevant to the bug/issue she's investigating. However, here are
    some examples of commit-messages that mention the area/subsystem:\
    -   "CRM\_Core\_Error - Cleanup log format"
    -   "api/v3/Email - Remove unused variable"
    -   "api/v3 - Fix various comment blocks"
    -   "civicrm/contact/view - fix 5.4 static errors"
