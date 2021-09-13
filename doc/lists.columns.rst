.. _columns:

columns — Convert multicolumn file to separate files
====================================================

**Package: lists**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  columns -- break a multicolumn list into multiple single column lists
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  columns filename numcols 
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>filename</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filename' Line='filename'>
  <DD>Name of the input table file.
  </DD>
  </DL>
  <DL>
  <DT><B>numcols</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='numcols' Line='numcols'>
  <DD>The number of columns in the input file.
  </DD>
  </DL>
  <DL>
  <DT><B>outroot = "<TT>col.</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outroot' Line='outroot = "col."'>
  <DD>Root name of the output column files.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>columns</I> is used to reformat a multicolumn list file into separate
  files, such that one output file is created for each column in the input
  file.  It is used to break multicolumn tables into simple CL lists.
  Comment lines beginning with  the character "<TT>#</TT>" are ignored.  All data
  is transferred as text.  One file <B>outroot</B>n is produced for each
  column in the input table.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Make 3 files named datacol.1, datacol.2 and datacol.3 from the 3 column
  table dtable:
  <PRE>
  <P>
      cl&gt; columns dtable 3 outroot=datacol.
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fields
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
