.. _copy:

copy: Copy a file or files (use IMCOPY for imagefiles)
======================================================

**Package: system**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  copy input output
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The input file or list of files to be copied.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>The (new) output file when copying one file to another, or the destination
  directory when copying a set of files.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>If set to <span style="font-family: monospace;">"yes"</span>, a line of the type <span style="font-family: monospace;">" from -&gt; to "</span> is printed on the
  terminal for each file copied to a directory.  This parameter is not
  used when copying one file to another.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Copy makes a copy of a single file, or it copies a set of files to a different
  directory.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Copy all files in the current directory with extension <span style="font-family: monospace;">".x"</span> to the
  directory <span style="font-family: monospace;">"home$src"</span>.  As each copy is made, the user is informed.
  </p>
  <p>
  	cl&gt; copy *.x home$src ver+
  </p>
  <p>
  2. Make a copy <span style="font-family: monospace;">"fred.BAK"</span> of the file <span style="font-family: monospace;">"fred"</span>.
  </p>
  <p>
  	cl&gt; copy fred fred.BAK
  </p>
  <p>
  3. Copy the <span style="font-family: monospace;">"graphcap"</span> file from the remote node <span style="font-family: monospace;">"lyra"</span> to the current node,
  without changing the name of the file.  Note that <span style="font-family: monospace;">"."</span> is a synonym for the
  current directory.
  </p>
  <p>
  	cl&gt; copy lyra!dev$graphcap .
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  concatenate, movefiles
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
