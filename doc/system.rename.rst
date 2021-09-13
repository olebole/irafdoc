.. _rename:

rename — Rename a file
======================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rename -- rename a file or set of files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rename file newname
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>file</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='file' Line='file'>
  <DD>A template specifying the file or files to be renamed.
  </DD>
  </DL>
  <DL>
  <DT><B>newname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newname' Line='newname'>
  <DD>If a single file is being renamed, the new filename, else the new name of
  the field being renamed in a set of filenames.  If <I>newname</I> is a
  directory the input files will be moved to this directory with the same
  name.
  </DD>
  </DL>
  <DL>
  <DT><B>field = all</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='field' Line='field = all'>
  <DD>If set to "<TT>all</TT>" the file name remains unchanged and the <I>newname</I> is
  assumed to be a destination directory in the case of multiple input files,
  or the new filename (which may contain a new directory path) in the case of
  a single input file.  If set to <I>ldir</I> the <I>newname</I> value is taken
  to be a destination directory and the file is moved to this directory.
  Setting to <I>root</I> will rename only the root portion of the filename,
  a value of <I>extn</I> will change or append the extension. <I>newname</I>
  cannot contain a directory path when changing the root or extn field.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Rename</I> renames either a single file to "<TT>newname</TT>", or a set of files,
  changing either the ldir, root or the extension part of each name.  
  If <I>newname</I> is a directory or  <I>field</I> is "<TT>ldir</TT>" the input files
  are moved to this directory and the filenames remain the same.  When
  modifying the root or extension part of the filename <I>newname</I> is the
  new root or extension name for the input files, an extension will be added
  to the file name if it doesn't already exist and the extension field is being
  modified.  For multiple input files it is assumed
  that <I>newname</I> is a directory if the value of <I>field</I> is "<TT>all</TT>", 
  otherwise an error is generated to prevent overwriting files.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Rename file "<TT>fred</TT>" to "<TT>jay</TT>".
  <P>
      cl&gt; rename fred jay
  <P>
  2. Change the root name of a set of files from "<TT>out</TT>" to "<TT>pkout</TT>".
  <P>
      cl&gt; rename out.x,out.o,out.par pkout field=root
  <P>
  3. Change the extension of all "<TT>.f77</TT>" files from "<TT>.f77</TT>" to "<TT>.f</TT>".
  <P>
      cl&gt; rename *.f77 f field=extn
  <P>
  4. Move all files with a "<TT>.dat</TT>" extension to a new directory.
  <P>
      cl&gt; rename *.dat data$
      cl&gt; rename *.dat /data/user
  <P>
  5. Add a "<TT>.fits</TT>" extension to all files in a directory.
  <P>
      cl&gt; rename im00* fits field=extn
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  movefiles, copy
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
