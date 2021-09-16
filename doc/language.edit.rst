.. _edit:

edit — Edit a text file
=======================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  edit -- edit a text file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  edit files [files...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>The file or files to be edited.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>edit</I> task invokes a host system editor to edit the named file or
  files.  The editor to be used is determined by the value of the CL environment
  variable <I>editor</I>.  Filename mapping is applied to the <I>files</I>
  argument strings to convert virtual filenames into host system filenames.
  File templates are not supported, unless the host system editor supports them.
  <P>
  The EDT, EMACS, and VI editors are currently supported.  Each editor interface
  is controlled by an <I>edcap</I> table file in the logical directory "<TT>dev$</TT>";
  these files are also used by the <I>ehistory</I> and <I>eparam</I> screen
  editors.  For example, the file "<TT>dev$edt.ed</TT>" is required to run the EDT
  editor.  The EDITOR_CMD field of the <I>edcap</I> file defines the command
  to be send to the host system to run the editor; this is not necessarily the
  same as the name of the editor.  Support for additional editors is easily added
  by adding new <I>edcap</I> files.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Edit the login.cl file.
  <P>
  	cl&gt; edit home$login.cl
  <P>
  2. Edit the file "<TT>temp</TT>" in the current directory.
  <P>
  	cl&gt; edit temp
  <P>
  3. On a UNIX system, edit all the "<TT>.x</TT>" files in the current directory.
  Filename templates cannot be used with the editor unless the editor itself,
  or the host system, expands the filename template.
  <P>
  	cl&gt; edit *.x
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The EOF control character is set in the edcap file for the editor language in
  use, e.g., "<TT>dev$vi.ed</TT>" for the VI editor.  The value in this file may differ
  from that used on the local system; if this is the case, the system installer
  should edit the file and change the value of the parameter EXIT_UPDATE.
  <P>
  The control sequences for the keyboard arrow keys are also defined in the
  "<TT>.ed</TT>" edcap file; TERMCAP should be used instead.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ehistory, eparam
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
