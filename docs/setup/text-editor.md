# Text editor settings to meet coding standards

Developers can make it easier to create code that meets the CiviCRM
Coding Standards by configuring their tools to automatically do some
things for them, such as whitespace formatting.

## Atom

1. Make sure `phpcs` is in your path.

1. Run the following command to add the *Drupal* standard (assuming you have [Buildkit](https://github.com/civicrm/civicrm-buildkit) installed:

        phpcs --config-set installed_paths /path/to/buildkit/vendor/drupal/coder/coder_sniffer

    - If you have [coder](https://github.com/civicrm/coder) installed without using Buildkit, use the path to the `coder_sniffer` directory within it.  The result is that you should see "Drupal" among the coding standards when you type `phpcs -i`.

1. Install the following packages in Atom: linter, linter-jshint, linter-php, linter-phpcs

1. In the editor settings, make sure "Soft Tabs" is checked and the "Tab Length" is *2*.

1. In the settings for the linter-phpcs packages, set the "Code Standard or Config File" as *Drupal*.

Some other useful packages, in addition to those listed above, include:
atom-autocomplete-php, docblockr, git-control, language-smarty-php, and
linter-jscs.

## Emacs

See Drupal's [recommended emacs settings](http://drupal.org/project/emacs).

## NetBeans

See Drupal's pages on
[Configuring NetBeans](http://drupal.org/node/1019816) and
[Netbeans Integration](http://drupal.org/node/1420008).

## PHPStorm

Create the 'CiviCRM' code styling preference:

1.  Open you current project's properties: File > Settings
1.  Create the CiviCRM code styling preference: Code Style > Manage >
    Save as, then indicate 'CiviCRM'
1.  In the 'Code style' sub-menu, select 'PHP', then 'Set from ...' at
    the far right, Predefined Style > Drupal (this sets options across
    all tabs of the dialog)
1.  In the 'Code style' sub-menu, select 'Javascript', then 'Set from
    ...' at the far right, PHP (this replicates all PHP settings to the
    Javascript section)
1.  Click 'Apply' at the bottom of the screen

That's it. You can now use this code style on all future CiviCRM-related
projects. If you are only developing for CiviCRM, you can also copy this
style to the 'Default' style.

## Sublime Text

See this
[Sublime build script](https://github.com/sirkitree/DrupalCodingStandard)
for running Drupal Code Sniffer.

## vim

See Drupal's page on [Configuring vim](http://drupal.org/node/29325).

## Zend Studio (Eclipse)

Configure your install as follows:

1.  Open Zend Studio.
2.  Click Zend Studio > Preferences...
3.  Open General > Editors > Text Editors.
    1.  In Displayed tab width, enter 2.
    2.  Click to enable Insert spaces for tabs.
4.  Open General > Workspace.
    1.  In Text file encoding, enable Other, and select UTF-8.
    2.  In New text file line delimiter, enable Other, and select Unix.
5.  Open PHP > Code Style > Code Templates.
    1.  Download the attachment from this wiki page titled CiviCRM
        codetemplates.xml
    2.  Click Import, select CiviCRM codetemplates.xml from your local
        drive, and Open to upload.
6.  Open PHP > Code Style > Formatter.
    1.  Download the attachment from this wiki page titled CiviCRM PHP
        Conventions.xml
    2.  Click Import, select CiviCRM PHP Conventions.xml, and Open to
        upload.
7.  Open PHP > Editor > Typing.
    1.  Disable Close PHP tag `?>`.
    2.  Enable Add "php" after PHP start tag `<?`.
8.  Open PHP > Editor > Save Actions.
    1.  Enable Remove Trailing Whitespace.
    2.  Choose All Lines.
