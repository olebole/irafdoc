.. _ehistory:

ehistory: Edit history file to re-execute commands
==================================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  ehistory -- edit and re-execute previous commands
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  ehistory (or just <tt>"e"</tt>)
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <p>
  None.
  </p>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>ehistory</i> command calls up a screen editor to edit previously
  executed commands, executing the edited command when return is typed.
  Interrupt (e.g., &lt;ctrl/c&gt; may be used to escape from the editor at any time.
  The type of editor commands recognized is determined by the value of the
  CL environment variable <i>editor</i>, which may currently be set to
  <tt>"edt"</tt>, <tt>"emacs"</tt>, or <tt>"vi"</tt>.
  </p>
  <p>
  After the <i>ehistory</i> command is entered, the previous command is
  displayed at the bottom of the terminal.  If the previous command was
  a compound statement, or if it extended over more than one line,
  all the lines of the command will be displayed.  To reach a different
  command simply enter the appropriate cursor movement keys for the editor type
  being used.  When the cursor attempts to move above the current command
  the previous command will be displayed.  Similarly when it attempts
  to move below, the next command will appear.  Hitting the return
  key will execute the command currently being edited.
  </p>
  <p>
  The CL parameter <tt>"ehinit"</tt> may be used to set the following options:
  </p>
  <dl>
  <dt><b>[no]standout</b></dt>
  <!-- Sec='DESCRIPTION' Level=0 Label='' Line='[no]standout' -->
  <dd>Controls whether the command to be edited is displayed in reverse or
  normal video.
  </dd>
  </dl>
  <dl>
  <dt><b>eol</b></dt>
  <!-- Sec='DESCRIPTION' Level=0 Label='eol' Line='eol' -->
  <dd>The editor is entered with the cursor positioned to be end of the command line.
  </dd>
  </dl>
  <dl>
  <dt><b>bol</b></dt>
  <!-- Sec='DESCRIPTION' Level=0 Label='bol' Line='bol' -->
  <dd>The editor is entered with the cursor positioned to be beginning of the command
  line.
  </dd>
  </dl>
  <dl>
  <dt><b>[no]verify</b></dt>
  <!-- Sec='DESCRIPTION' Level=0 Label='' Line='[no]verify' -->
  <dd>If <i>verify</i> is specified, <i>ehistory</i> will be automatically entered
  when history commands are entered to recall and execute previous commands.
  If <i>noverify</i> is specified, the commands are recalled and immediately
  executed.
  </dd>
  </dl>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Set no standout and verify modes. 
  </p>
  <p>
  	cl&gt; ehinit = <tt>"nostandout verify"</tt>.
  </p>
  <p>
  2. Recall the last <tt>"xc"</tt> command from the history list and edit it.
  If <i>verify</i> were not enabled the command would simply be repeated.
  </p>
  <p>
  	cl&gt; ^xc
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  The command editor really only works well for single line commands;
  multiline command blocks are not easily edited at present.
  VI is poorly emulated at present since only control code editor commands
  are possible.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  eparam
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
