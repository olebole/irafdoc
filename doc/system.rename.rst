.. _rename:

rename: Rename a file
=====================

**Package: system**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  rename -- rename a file or set of files
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  rename file newname
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>file</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='file' Line='file' -->
  <dd>A template specifying the file or files to be renamed.
  </dd>
  </dl>
  <dl>
  <dt><b>newname</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='newname' Line='newname' -->
  <dd>If a single file is being renamed, the new filename, else the new name of
  the field being renamed in a set of filenames.  If <i>newname</i> is a
  directory the input files will be moved to this directory with the same
  name.
  </dd>
  </dl>
  <dl>
  <dt><b>field = all</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='field' Line='field = all' -->
  <dd>If set to <tt>"all"</tt> the file name remains unchanged and the <i>newname</i> is
  assumed to be a destination directory in the case of multiple input files,
  or the new filename (which may contain a new directory path) in the case of
  a single input file.  If set to <i>ldir</i> the <i>newname</i> value is taken
  to be a destination directory and the file is moved to this directory.
  Setting to <i>root</i> will rename only the root portion of the filename,
  a value of <i>extn</i> will change or append the extension. <i>newname</i>
  cannot contain a directory path when changing the root or extn field.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  <i>Rename</i> renames either a single file to <tt>"newname"</tt>, or a set of files,
  changing either the ldir, root or the extension part of each name.  
  If <i>newname</i> is a directory or  <i>field</i> is <tt>"ldir"</tt> the input files
  are moved to this directory and the filenames remain the same.  When
  modifying the root or extension part of the filename <i>newname</i> is the
  new root or extension name for the input files, an extension will be added
  to the file name if it doesn't already exist and the extension field is being
  modified.  For multiple input files it is assumed
  that <i>newname</i> is a directory if the value of <i>field</i> is <tt>"all"</tt>, 
  otherwise an error is generated to prevent overwriting files.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Rename file <tt>"fred"</tt> to <tt>"jay"</tt>.
  </p>
  <p>
      cl&gt; rename fred jay
  </p>
  <p>
  2. Change the root name of a set of files from <tt>"out"</tt> to <tt>"pkout"</tt>.
  </p>
  <p>
      cl&gt; rename out.x,out.o,out.par pkout field=root
  </p>
  <p>
  3. Change the extension of all <tt>".f77"</tt> files from <tt>".f77"</tt> to <tt>".f"</tt>.
  </p>
  <p>
      cl&gt; rename *.f77 f field=extn
  </p>
  <p>
  4. Move all files with a <tt>".dat"</tt> extension to a new directory.
  </p>
  <p>
      cl&gt; rename *.dat data$
      cl&gt; rename *.dat /data/user
  </p>
  <p>
  5. Add a <tt>".fits"</tt> extension to all files in a directory.
  </p>
  <p>
      cl&gt; rename im00* fits field=extn
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  movefiles, copy
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  -->
  
