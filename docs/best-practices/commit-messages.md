# Writing good commit messages in git

## Basic standards

Commit messages appear in many contexts -- e.g. in `git log`, `gitk`,
GitHub, Jenkin's test runs, email notifications, and JIRA's *Commits*
tab. To ensure that a commit message is easy to read in all contexts, it
should generally:

-   Start with a meaningful one-line summary.
-   Include a reference to a JIRA issue.

## Using git-footnote to save time

To make the process of writing useful commit messages faster and easier,
we have a tool called
[git-footnote](https://github.com/totten/git-footnote)
that automatically adds details to your commit message according to the
following logic.

-   Any time you reference a JIRA issue in any part of a commit message,
    git-footnote will look up the issue and append a hyperlink to the
    commit message.
-   If you write a 1-2 word commit message ("CRM-1234" or "fix
    CRM-1234"), git-footnote will put the JIRA issue title in the summary
    line.


## git-footnote examples

Below are some examples of good and bad commit messages, and how git-footnote
works its magic on them.

!!! note
    The first line is often the only line displayed when browsing through
    commits, so pay particular attention to it.


### Awesome example

Your Commit Message:

```text
CRM-1234 - Subsystem - Summarize what the commit does

Also write a longer explanation of what the commit does. You don't need to give
a detailed lesson on how everything works, but it may help to describe the
corner-case or obscure interaction you were thinking about, or it may help to
reference other relevant issues (like CRM-4567 or CRM-8901). Add whatever seems
useful.
```

Final Commit Message (after running git-footnote):

```text
CRM-1234 - Subsystem - Summarize what the commit does

Also write a longer explanation of what the commit does. You don't need to give
a detailed lesson on how everything works, but it may help to describe the
corner-case or obscure interaction you were thinking about, or it may help to
reference other relevant issues (like CRM-4567 or CRM-8901). Add whatever seems
useful.

---
  * CRM-1234: The Issue Title From JIRA
    http://issues.civicrm.org/jira/browse/CRM-1234
  * CRM-4567: The Other Issue Title From JIRA
    http://issues.civicrm.org/jira/browse/CRM-4567
  * CRM-8901: The Third Issue Title From JIRA
    http://issues.civicrm.org/jira/browse/CRM-8901
```

### Great example

Your Commit Message:

```text
CRM-1234 - Subsystem - Summarize what the commit does
```
Final Commit Message (after running git-footnote):

```text
CRM-1234 - Subsystem - Summarize what the commit does

---

 * CRM-1234: The Issue Title From JIRA
   http://issues.civicrm.org/jira/browse/CRM-1234
```

### Good example

Your Commit Message:

```text
CRM-1234 - Summarize what the commit does
```

Final Commit Message (after running git-footnote):

```text
CRM-1234 - Summarize what the commit does

---

 * CRM-1234: The Issue Title From JIRA
   http://issues.civicrm.org/jira/browse/CRM-1234
```

### OK example

Your Commit Message:

```text
CRM-1234
```

Final Commit Message (after running git-footnote):

```text
CRM-1234 - The Issue Title From JIRA
http://issues.civicrm.org/jira/browse/CRM-1234
```

### OK example

Your Commit Message:

```text
fix CRM-1234
```

Final Commit Message (after running git-footnote):

```text
fix CRM-1234 - The Issue Title From JIRA
http://issues.civicrm.org/jira/browse/CRM-1234
```

### OK example

Your Commit Message:

```text
Subsystem - Summarize what the commit does
```

*(git-footnote does not change commit message)*

### So-So example

Your Commit Message:

```text
Summarize what the commit does
```

*(git-footnote does not change commit message)*


### Terrible example

Your Commit Message:

```text
cleanup
```

*(git-footnote does not change commit message)*


## Installing git-footnote

Git-footnote works by using
[git hooks](http://git-scm.com/book/en/Customizing-Git-Git-Hooks).

To take advantage of the automatic formatting on commit messages, you must
enable CiviCRM's git hooks
The "gitify" tool (discussed in
[Contributing to CiviCRM using GitHub](/confluence/display/CRMDOC/Contributing+to+CiviCRM+using+GitHub))
will create the hooks if you include the "--hooks" option. If you didn't
originally use "gitify" with the "–hooks" option, then just re-run
"gitify" and add the "--hooks" option this time. ("gitify" won't replace
your existing git repos, but it will register hooks on them.)

If you cannot or do not want to use "gitify", then you can
[review the standard git hooks included with CiviCRM](https://github.com/civicrm/civicrm-core/tree/master/tools/scripts/git)
and write your own. Be sure to look at each of your git repositories
("civicrm-core", "civicrm-drupal", etc) to ensure the hooks are
registered.

## FAQ

-   **Q: What if I write something that doesn't have a JIRA issue?**
-   A: It's generally good practice to create a JIRA issue before
    working on a problem, then reference the issue in the commit
    message. However, if that seems inappropriate, then make reference
    to the general **area or subsystem** instead.
-   **Q: What is an "area" or "subsystem"?**
-   A: The term is purposefully ambiguous - it's difficult to think of a
    hard rule, and it seems to depend on how many lines/files/functions
    were touched. It might be the name of a class, a function, a
    template, a directory, or a component. The goal is the provide some
    clue to the future reader so that she can guess which commits would
    be relevant to the bug/issue she's investigating. However, here are
    some examples of commit-messages that mention the area/subsystem:
    -   `CRM_Core_Error - Cleanup log format`
    -   `apiv3Email - Remove unused variable`
    -   `apiv3 - Fix various comment blocks`
    -   `civicrm/contact/view - fix 5.4 static errors`
