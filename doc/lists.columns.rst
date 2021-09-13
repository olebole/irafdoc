columns — Convert multicolumn file to separate files
====================================================

**Package: lists**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>columns (Nov88)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>lists</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>columns (Nov88)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>columns</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  columns -- break a multicolumn list into multiple single column lists
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  columns filename numcols 
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_filename">filename</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filename' Line='filename'>
  <DD>Name of the input table file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_numcols">numcols</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='numcols' Line='numcols'>
  <DD>The number of columns in the input file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outroot">outroot = "<TT>col.</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outroot' Line='outroot = "col."'>
  <DD>Root name of the output column files.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
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
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
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
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fields
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>