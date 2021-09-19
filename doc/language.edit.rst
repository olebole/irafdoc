.. _edit:

edit: Edit a text file
======================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  edit -- edit a text file
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  edit files [files...]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>files</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='files' Line='files' -->
  <dd>The file or files to be edited.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>edit</i> task invokes a host system editor to edit the named file or
  files.  The editor to be used is determined by the value of the CL environment
  variable <i>editor</i>.  Filename mapping is applied to the <i>files</i>
  argument strings to convert virtual filenames into host system filenames.
  File templates are not supported, unless the host system editor supports them.
  </p>
  <p>
  The EDT, EMACS, and VI editors are currently supported.  Each editor interface
  is controlled by an <i>edcap</i> table file in the logical directory <tt>"dev$"</tt>;
  these files are also used by the <i>ehistory</i> and <i>eparam</i> screen
  editors.  For example, the file <tt>"dev$edt.ed"</tt> is required to run the EDT
  editor.  The EDITOR_CMD field of the <i>edcap</i> file defines the command
  to be send to the host system to run the editor; this is not necessarily the
  same as the name of the editor.  Support for additional editors is easily added
  by adding new <i>edcap</i> files.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Edit the login.cl file.
  </p>
  <p>
  	cl&gt; edit home$login.cl
  </p>
  <p>
  2. Edit the file <tt>"temp"</tt> in the current directory.
  </p>
  <p>
  	cl&gt; edit temp
  </p>
  <p>
  3. On a UNIX system, edit all the <tt>".x"</tt> files in the current directory.
  Filename templates cannot be used with the editor unless the editor itself,
  or the host system, expands the filename template.
  </p>
  <p>
  	cl&gt; edit *.x
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The EOF control character is set in the edcap file for the editor language in
  use, e.g., <tt>"dev$vi.ed"</tt> for the VI editor.  The value in this file may differ
  from that used on the local system; if this is the case, the system installer
  should edit the file and change the value of the parameter EXIT_UPDATE.
  </p>
  <p>
  The control sequences for the keyboard arrow keys are also defined in the
  <tt>".ed"</tt> edcap file; TERMCAP should be used instead.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  ehistory, eparam
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
