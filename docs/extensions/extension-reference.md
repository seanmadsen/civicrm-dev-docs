# Extension Reference

<div class="panel"
style="background-color: #FFFFCE;border-color: #000;border-style: solid;border-width: 1px;">

<div class="panelHeader"
style="border-bottom-width: 1px;border-bottom-style: solid;border-bottom-color: #000;background-color: #F7D6C1;">

**Table of Contents**

</div>

<div class="panelContent" style="background-color: #FFFFCE;">

<div>

-   [Introduction](#ExtensionReference-Introduction)
-   [Changelog](#ExtensionReference-Changelog)
-   [Packaging](#ExtensionReference-Packaging)
-   [Tags in info.xml](#ExtensionReference-Tagsininfo.xml)

<!-- -->

-   [Choose unique key for your
    extension](#ExtensionReference-Chooseuniquekeyforyourextension)
-   [Custom search specific typeInfo
    fields](#ExtensionReference-CustomsearchspecifictypeInfofields)
-   [Report template specific typeInfo
    fields](#ExtensionReference-ReporttemplatespecifictypeInfofields)
-   [Payment processor specific typeInfo
    fields](#ExtensionReference-PaymentprocessorspecifictypeInfofields)

<!-- -->

-   [Example XML - type =
    Module](#ExtensionReference-ExampleXML-type=Module)

</div>

</div>

</div>

# Introduction

A ***native CiviCRM extension*** is a feature provided by a third-party
developer which can be installed on CiviCRM. To support automated
distribution and installation, an extension must be packaged according
to a particular specification. This page documents the technical
structure of an extension. For a proper introduction to developing
extensions, see [Create an
Extension](/confluence/display/CRMDOC/Create+an+Extension).

# Changelog

<div class="table-wrap">

  CiviCRM Version   Description
  ----------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  4.5               &lt;develStage&gt; is not always required; when using civicrm.org's automated release management, this value is inferred from the version; for manual or private releases, the field should still be defined.
  4.2               Most extensions should be packaged as generic *module* rather than type-specific extensions.
  4.2               &lt;downloadUrl&gt; is optional for ordinary development; when using civicrm.org to distribute extensions, the &lt;downloadUrl&gt; will be specified when announcing the release on the website
  4.2               &lt;downloadUrl&gt; can point to auto-generated zipballs on Github.com
  4.2               Introduce stable support for generic modules.
  4.1               Introduce experimental extension-type for generic modules*.*
  3.3               Introduce extension-types for payment-processors, report-templates, and custom-searches.

</div>

# Packaging

For redistribution, an extension must be packaged as a .zip file which
meets these requirements:

-   All content in the .zip must be stored under a single folder. The
    folder should match the extension's unique key. (In 4.1 and earlier,
    the matched name was mandatory. In 4.2 and later, the matched name
    is optional.)
-   The folder must include a file named "info.xml" which meets the
    specification below.

# Tags in info.xml

<div class="table-wrap">

+--------------------------+--------------------------+--------------------------+
| element name             | description              | required?                |
+==========================+==========================+==========================+
| **extension**            | enclosing element for    | **YES**                  |
|                          | all the information in   |                          |
|                          | info.xml - everything    |                          |
|                          | needs to sit inside of   |                          |
|                          | it. Attributes are:      |                          |
|                          |                          |                          |
|                          | 1.  **key**: unique name |                          |
|                          |     of the extension     |                          |
|                          |     (should match the    |                          |
|                          |     name of directory    |                          |
|                          |     this extension       |                          |
|                          |     resides in). See     |                          |
|                          |     information on       |                          |
|                          |     choosing the         |                          |
|                          |     extension key below  |                          |
|                          |     for                  |                          |
|                          |     more information.    |                          |
|                          | 2.  **type**: one of     |                          |
|                          |     "module", "search",  |                          |
|                          |     "payment", "report", |                          |
|                          |     meaning that this    |                          |
|                          |     extension is -       |                          |
|                          |     respectively - a     |                          |
|                          |     custom module,       |                          |
|                          |     search, payment      |                          |
|                          |     processor or         |                          |
|                          |     custom report.       |                          |
+--------------------------+--------------------------+--------------------------+
| **downloadUrl**          | the url to the zip file  | **NO\                    |
|                          | with your extension.     | **                       |
|                          |                          |                          |
|                          | *NOTE: Prior to CiviCRM  |                          |
|                          | 4.2, the downloadUrl was |                          |
|                          | mandatory in info.xml.   |                          |
|                          | It needed to point to a  |                          |
|                          | plain .zip file whose    |                          |
|                          | content included a base  |                          |
|                          | folder; and it was       |                          |
|                          | mandatory for the base   |                          |
|                          | folder to be named after |                          |
|                          | the extension.\          |                          |
|                          | *                        |                          |
|                          |                          |                          |
|                          | *NOTE: Beginning with    |                          |
|                          | CiviCRM 4.2, developers  |                          |
|                          | should not normally      |                          |
|                          | include the downloadUrl. |                          |
|                          | The information will     |                          |
|                          | only be required when    |                          |
|                          | submitting a new release |                          |
|                          | on civicrm.org.\         |                          |
|                          | *                        |                          |
+--------------------------+--------------------------+--------------------------+
| **file**                 | the name of the file to  | **YES**                  |
|                          | invoke when extension is |                          |
|                          | executed (not including  |                          |
|                          | .php file extension).    |                          |
|                          | This file must be        |                          |
|                          | present in the root of   |                          |
|                          | the extension .zip file  |                          |
|                          | / in base directory of   |                          |
|                          | the extension.           |                          |
|                          |                          |                          |
|                          | EXAMPLE:                 |                          |
|                          | &lt;file&gt;sagepay&lt;/ |                          |
|                          | file&gt;.                |                          |
|                          | Extension zip file and   |                          |
|                          | extension base directory |                          |
|                          | contain *sagepay.php*    |                          |
+--------------------------+--------------------------+--------------------------+
| **name**                 | name of the extension    | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **label**                | label of the extension.  | **NO**                   |
|                          | For search extensions,   |                          |
|                          | this tag is used as the  |                          |
|                          | menu item text on Custom |                          |
|                          | Searches list.           |                          |
+--------------------------+--------------------------+--------------------------+
| **description**          | description of the       | **YES**                  |
|                          | extension                |                          |
+--------------------------+--------------------------+--------------------------+
| **urls**                 | a section containing all | **YES/NO**               |
|                          | the urls that you think  |                          |
|                          | are appropriate and      |                          |
|                          | necessary for users to   |                          |
|                          | find out more about what |                          |
|                          | your extension does,     |                          |
|                          | additional               |                          |
|                          | documentation, etc. It's |                          |
|                          | made of multiple **url** |                          |
|                          | elements                 |                          |
+--------------------------+--------------------------+--------------------------+
| general                  | **url** contains links   | **NO**                   |
|                          | and has one attribute:   |                          |
|                          | **desc** - the title to  |                          |
|                          | be used when the link is |                          |
|                          | displayed.               |                          |
+--------------------------+--------------------------+--------------------------+
| documentation            | **&lt;url**              | **YES**                  |
|                          | **desc="documentation"&g |                          |
|                          | t;link                   |                          |
|                          | to online documentation  |                          |
|                          | here&lt;/url&gt;**       |                          |
+--------------------------+--------------------------+--------------------------+
| **license**              | the name of the license  | **YES**                  |
|                          | under which your         |                          |
|                          | extension is offered.    |                          |
|                          | For more information on  |                          |
|                          | what license to choose,  |                          |
|                          | see [CiviCRM licensing   |                          |
|                          | page](http://civicrm.org |                          |
|                          | /licensing){.external-li |                          |
|                          | nk}.                     |                          |
|                          | For technical details on |                          |
|                          | how to identify a        |                          |
|                          | license, see [SPDX       |                          |
|                          | License                  |                          |
|                          | List](http://www.spdx.or |                          |
|                          | g/licenses/){.external-l |                          |
|                          | ink}.                    |                          |
+--------------------------+--------------------------+--------------------------+
| **maintainer**           | a section describing     | **YES**                  |
|                          | maintainer information.  |                          |
|                          | It has two elements:     |                          |
+--------------------------+--------------------------+--------------------------+
|                          | **author** - name of the | **YES**                  |
|                          | person and/or            |                          |
|                          | organisation maintaining |                          |
|                          | the extension            |                          |
+--------------------------+--------------------------+--------------------------+
|                          | **email** - extension    | **YES**                  |
|                          | maintainer's email       |                          |
|                          | address                  |                          |
+--------------------------+--------------------------+--------------------------+
| **releaseDate**          | date of release (use     | **YES**                  |
|                          | *yyyy-mm-dd* format)     |                          |
+--------------------------+--------------------------+--------------------------+
| **version**              | version of this          | **YES**                  |
|                          | extension (used for      |                          |
|                          | upgrade detection and    |                          |
|                          | used to sort available   |                          |
|                          | releases for automated   |                          |
|                          | distribution)            |                          |
|                          |                          |                          |
|                          | Valid version formats    |                          |
|                          | include:                 |                          |
|                          |                          |                          |
|                          |     '1', '1.1', '1.2.3.4 |                          |
|                          | ', '1.2-3', '1.2.alpha2' |                          |
|                          | , '1.2.rc2', '2012-01-01 |                          |
|                          | -1', '2012-01-01', 'r456 |                          |
|                          | ', 'r5000'               |                          |
+--------------------------+--------------------------+--------------------------+
| **develStage**           | development stage - one  | **YES/NO**               |
|                          | of: "stable", "beta",    |                          |
|                          | "alpha". By default, the |                          |
|                          | in-app distribution      |                          |
|                          | system will only         |                          |
|                          | publicize "stable"       |                          |
|                          | releases.                |                          |
|                          |                          |                          |
|                          | If using  civicrm.org's  |                          |
|                          | automated release        |                          |
|                          | management (based on git |                          |
|                          | tags), the               |                          |
|                          | &lt;develStage&gt; will  |                          |
|                          | be determined            |                          |
|                          | automatically by         |                          |
|                          | searching for "alpha" or |                          |
|                          | "beta" in the version.   |                          |
+--------------------------+--------------------------+--------------------------+
| **compatibility**        | section describing       | **YES**                  |
|                          | CiviCRM version          |                          |
|                          | compatibility, it's made |                          |
|                          | of multiple **ver**      |                          |
|                          | elements - one for each  |                          |
|                          | supported CiviCRM        |                          |
|                          | version, e.g.            |                          |
|                          | &lt;ver&gt;4.2&lt;/ver&g |                          |
|                          | t;&lt;ver&gt;4.3&lt;/ver |                          |
|                          | &gt;                     |                          |
+--------------------------+--------------------------+--------------------------+
|                          | **ver** - element        | **YES**                  |
|                          | containing CiviCRM       |                          |
|                          | version (two digits with |                          |
|                          | a dot between them) that |                          |
|                          | this extension is        |                          |
|                          | compatible with, the     |                          |
|                          | allowed values are       |                          |
|                          | currently: 2.2, 3.0,     |                          |
|                          | 3.1, 3.2, 3.3, 3.4, 4.0, |                          |
|                          | 4.1, 4.2, 4.3, 4.4       |                          |
+--------------------------+--------------------------+--------------------------+
| **comments**             | additional comments      | **NO**                   |
+--------------------------+--------------------------+--------------------------+
| **typeInfo**             | section with type        | **YES/NO**               |
|                          | specific extension       |                          |
|                          | information. Each        |                          |
|                          | extension type has       |                          |
|                          | different set of fields  |                          |
|                          | required here - please   |                          |
|                          | refer to further parts   |                          |
|                          | of this document for     |                          |
|                          | details.                 |                          |
+--------------------------+--------------------------+--------------------------+

</div>

## Choose unique key for your extension

Every extension has unique name called an **extension key**. It's built
using Java-like reverse domain naming to make it easier to identify
unique extensions.



<div class="panelMacro">

+--+
|  |
+--+

</div>

## Custom search specific typeInfo fields

Custom search extensions do not require typeInfo section in the info.xml
file.

## Report template specific typeInfo fields

<div class="table-wrap">

+--------------------------+--------------------------+--------------------------+
| element name             | description              | required?                |
+==========================+==========================+==========================+
| **reportUrl**            |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **reportUrl**            |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+

</div>

## Payment processor specific typeInfo fields

<div class="table-wrap">

+--------------------------+--------------------------+--------------------------+
| element name             | description              | required?                |
+==========================+==========================+==========================+
| **userNameLabel**        |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **passwordLabel**        |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **signatureLabel**       |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **subjectLabel**         |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **urlSiteDefault**       |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **urlApiDefault**        |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **urlRecurDefault**      |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **urlSiteTestDefault**   |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **urlApiTestDefault**    |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **urlRecurTestDefault**  |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **urlButtonDefault**     |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **urlButtonTestDefault** |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **billingMode**          |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **isRecur**              |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+
| **paymentType**          |                          | **YES**                  |
+--------------------------+--------------------------+--------------------------+

</div>

# Example XML - type = Module

Module is the preferred extension type for 4.2+. Modules can include
forms, form and pre/post processing modifications, custom searches,
payment processors, reports and more. Prior versions of this page
document the xml for the legacy format

<div class="code panel" style="border-width: 1px;">

<div class="codeContent panelContent">

    <extension key="eu.tttp.exportexcel" type="module">
      <file>exportexcel</file>
      <downloadUrl>http://github.com/TechToThePeople/eu.tttp.excel/archive/master.zip</downloadUrl>
      <name>Export to Excel</name>
      <description>Excel isn't very good at importing csv files. If you have screamed at your computer with weird characters, long lines of gibberish and hair pulling, this extension is for you.
     Technically, it isn't excel but an html table with a header that pretends to be excel. Close enough to trick excel to behave like it doesn't hate you too much.
      </description>
      <urls>
        <url desc="Main Extension Page">http://github.com/TechToThePeople/eu.tttp.excel</url>
        <url desc="Documentation">http://github.com/TechToThePeople/eu.tttp.excel</url>
        <url desc="Support">http://forum.civicrm.org</url><url desc="Licensing">http://civicrm.org/licensing</url>
      </urls>
      <license>AGPL v3</license>
      <maintainer>
        <author>xavier dutoit</author>
        <email>civicrm@tttp.eu</email>
      </maintainer>
      <releaseDate>2012-01-08</releaseDate>
      <version>1.2</version>
      <develStage>stable</develStage>
      <compatibility>
        <ver>4.1</ver>
        <ver>4.2</ver>
      </compatibility>
      <comments>Enable the extension and export, that's it</comments>
      <civix>
        <namespace>CRM/Exportexcel</namespace>
      </civix>
    </extension>

</div>

</div>