.. _history:

history: Display  commands previously executed
==============================================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  history -- display the last few commands
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  history [[-]ncommands]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>ncommands</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ncommands' Line='ncommands' -->
  <dd>The number of commands to be displayed.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The <i>history</i> task prints a list of the last few commands executed.
  Only commands which terminated normally are included.
  The number of commands to be printed may be specified on the command line
  if desired.  If the number is preceded by a minus sign the default
  number of lines is not changed, otherwise <i>history</i> will take the
  value given as the new default number of commands to be printed.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Print the last few commands.
  	
  	cl&gt; history
  </p>
  <p>
  2. Print the entire history list.
  </p>
  <p>
  	cl&gt; history -999
  </p>
  <p>
  3. Change the default number of history lines to be printed to 5 (and print
  the last five commands).
  </p>
  <p>
  	cl&gt; history 5
  </p>
  <p>
  4. Save the history in the file <tt>"commands"</tt>.
  </p>
  <p>
  	cl&gt; history -999 &gt; commands
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  ehistory
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
