.. _mkmanpage:

mkmanpage: Make a manual page
=============================

**Package: softools**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  mkmanpage -- create and edit a new manual page
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mkmanage module
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>module</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='module' Line='module' -->
  <dd>The name of the program to be documented, i.e., the name that will appear at
  the top of the manual page, and the root name of the <span style="font-family: monospace;">".hlp"</span> file to be
  created.
  </dd>
  </dl>
  <dl>
  <dt><b>clformat = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='clformat' Line='clformat = yes' -->
  <dd>Make a CL format manual page template?
  </dd>
  </dl>
  <dl>
  <dt><b>cltemplate = <span style="font-family: monospace;">"doc$mancl.hlp"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cltemplate' Line='cltemplate = "doc$mancl.hlp"' -->
  <dd>Filename of the template file for a CL manual page.
  </dd>
  </dl>
  <dl>
  <dt><b>xtemplate = <span style="font-family: monospace;">"doc$manx.hlp"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xtemplate' Line='xtemplate = "doc$manx.hlp"' -->
  <dd>Filename of the template file for a library procedure manual page.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>mkmanpage</i> task is used to create a fill-in-the-blanks type
  template, to be edited to create the manual page for the named help module
  or task.  Depending upon the type of manual page to be created, <i>mkmanpage</i>
  copies the template file to the current directory, creating a new file with
  the name <span style="font-family: monospace;">"module.hlp"</span>, where <i>module</i> is the name entered on the
  command line.  The editor is called up to edit the file and the task exits.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Make a new manual page for task <span style="font-family: monospace;">"page"</span>.
  </p>
  <p>
  	cl&gt; mkmanpage page
  </p>
  <p>
  The task creates a file <span style="font-family: monospace;">"page.hlp"</span> in the current directory, and calls
  up the editor to edit the new file.
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  mkhelpdb, help, lroff
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
