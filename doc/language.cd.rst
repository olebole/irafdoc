.. _cd:

cd: Change directory
====================

**Package: language**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  chdir, cd -- change the current working directory
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  chdir [newdir]  or  cd [newdir]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>newdir</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='newdir' Line='newdir' -->
  <dd>The new working directory.
  The special name <span style="font-family: monospace;">"."</span> refers to the current directory; <span style="font-family: monospace;">".."</span> refers to the next
  higher directory.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Chdir</i> is used to change the current working directory.
  When called without any arguments, <i>chdir</i> sets the default directory
  to <span style="font-family: monospace;">"home$"</span>, the users home directory.
  The new directory can be specified as an IRAF logical name,
  as a sub-directory of the current directory,
  as a path from either a logical directory or the current directory,
  or as an operating system dependent name.
  </p>
  <p>
  The names <i>chdir</i> and <i>cd</i> are synonyms.  Note that the command
  <i>back</i> may be called after a <i>chdir</i> to return to the previous
  directory without typing its name.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Return to our home directory.
  </p>
  <p>
  	cl&gt; cd
  </p>
  <p>
  2. Go to the package logical directory <span style="font-family: monospace;">"pkg$"</span>.
  </p>
  <p>
  	cl&gt; chdir pkg
  </p>
  <p>
  3. Go down one level to the directory <span style="font-family: monospace;">"dataio"</span>, a subdirectory of <span style="font-family: monospace;">"pkg"</span>.
  </p>
  <p>
  	cl&gt; cd dataio
  </p>
  <p>
  4. From <span style="font-family: monospace;">"dataio"</span>, go back up to <span style="font-family: monospace;">"pkg"</span> and down into <span style="font-family: monospace;">"images"</span>.
  </p>
  <p>
  	cl&gt; cd ../images
  </p>
  <p>
  5. Go to the <span style="font-family: monospace;">"tv"</span> directory, a subdirectory of <span style="font-family: monospace;">"images"</span>, regardless of the
  current directory
  </p>
  <p>
  	cl&gt; cd pkg$images/tv
  </p>
  <p>
  6. On a VMS system, define a new logical directory on a different disk device
  and go there.  Note that the character $ is not permitted in host file or
  directory names.
  </p>
  <pre>
  	cl&gt; set dd = scr1:[data]
  	cl&gt; cd dd
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  back, pathnames
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
