.. _mkmanpage:

mkmanpage — Make a manual page
==============================

**Package: softools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkmanpage -- create and edit a new manual page
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkmanage module
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>module</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='module' Line='module'>
  <DD>The name of the program to be documented, i.e., the name that will appear at
  the top of the manual page, and the root name of the "<TT>.hlp</TT>" file to be
  created.
  </DD>
  </DL>
  <DL>
  <DT><B>clformat = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clformat' Line='clformat = yes'>
  <DD>Make a CL format manual page template?
  </DD>
  </DL>
  <DL>
  <DT><B>cltemplate = "<TT>doc$mancl.hlp</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cltemplate' Line='cltemplate = "doc$mancl.hlp"'>
  <DD>Filename of the template file for a CL manual page.
  </DD>
  </DL>
  <DL>
  <DT><B>xtemplate = "<TT>doc$manx.hlp</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xtemplate' Line='xtemplate = "doc$manx.hlp"'>
  <DD>Filename of the template file for a library procedure manual page.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>mkmanpage</I> task is used to create a fill-in-the-blanks type
  template, to be edited to create the manual page for the named help module
  or task.  Depending upon the type of manual page to be created, <I>mkmanpage</I>
  copies the template file to the current directory, creating a new file with
  the name "<TT>module.hlp</TT>", where <I>module</I> is the name entered on the
  command line.  The editor is called up to edit the file and the task exits.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Make a new manual page for task "<TT>page</TT>".
  <P>
  	cl&gt; mkmanpage page
  <P>
  The task creates a file "<TT>page.hlp</TT>" in the current directory, and calls
  up the editor to edit the new file.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkhelpdb, help, lroff
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
