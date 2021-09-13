tabim — Copy a table column to an image.
========================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tabim (Mar2000)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tabim (Mar2000)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tabim</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tabim -- Copy a table column to an image.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tabim intable output colname ndim n1 n2 n3 n4 n5 n6
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task writes values from a column of a table to an image.
  If the image does not exist, it will be created.
  The value in the first row is assigned to the first pixel of the image,
  and the value in the last row is assigned to the last pixel of the image.
  Columns containing pixel numbers (optionally written by 'imtab') are ignored,
  but you can specify the axis lengths of a multi-dimensional output image.
  The number of rows in the table must equal the number of pixels in the image.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_intable">intable = "<TT></TT>" [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable = "" [file name template]'>
  <DD>The names of the input tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT></TT>" [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "" [file name template]'>
  <DD>The names of the output images.
  If an output image does not exist it will be created.
  If the image does exist it will be overwritten with values from the table.
  A section of an existing image may be specified,
  but note that the size must equal the number of rows in the table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_colname">colname = "<TT></TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='colname' Line='colname = "" [string]'>
  <DD>The name of the column in 'intable' that is to be written to the image.
  The same column name is used for all input tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ndim">ndim = 0 [integer, min=0, max=7]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ndim' Line='ndim = 0 [integer, min=0, max=7]'>
  <DD>If the output image does not exist,
  'ndim' can be used to specify
  the dimension of the image to be created.
  ndim = 0 or 1 results in a one-dimensional image
  which has as many elements as rows in the table.
  If 'ndim' is greater than one
  and the output image does not already exist,
  then the parameters 'n1', 'n2', etc will be taken
  to specify the axis lengths of the output image.
  The lengths of all but the last axis will be gotten from 'n1', 'n2', etc.;
  the last axis length will be computed from
  the number of rows in the table
  and the lengths of the other axes.
  It is an error if the product of the specified axis lengths
  does not divide evenly into the number of rows in the table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_n1">n1 = 1 [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='n1' Line='n1 = 1 [integer, min=1, max=INDEF]'>
  <DD>Length of first axis.
  'n1', 'n2', etc., are ignored if ndim = 0 or 1.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_n2">n2 = 1 [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='n2' Line='n2 = 1 [integer, min=1, max=INDEF]'>
  <DD>Length of second axis.
  This and the subsequent axis length parameters will be ignored if ndim &lt; 3.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_n3">n3 = 1 [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='n3' Line='n3 = 1 [integer, min=1, max=INDEF]'>
  <DD>Length of third axis.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_n4">n4 = 1 [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='n4' Line='n4 = 1 [integer, min=1, max=INDEF]'>
  <DD>Length of fourth axis.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_n5">n5 = 1 [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='n5' Line='n5 = 1 [integer, min=1, max=INDEF]'>
  <DD>Length of fifth axis.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_n6">n6 = 1 [integer, min=1, max=INDEF]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='n6' Line='n6 = 1 [integer, min=1, max=INDEF]'>
  <DD>Length of sixth axis.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Copy column "<TT>flux</TT>" from table "<TT>hr465.tab</TT>" to
  the 1-D image "<TT>hr465_flux.imh</TT>":
  <P>
  <PRE>
  	ta&gt; tabim hr465.tab hr465_flux.imh flux 1
  </PRE>
  <P>
  2.  Create a three-dimensional image "<TT>ir27.imh</TT>" of size 62 x 64 x 4.
  Read the values from column "<TT>v1</TT>" of table "<TT>t18_30.tab</TT>",
  which has 62*64*4 rows.
  <P>
  <PRE>
  	ta&gt; tabim t18_30.tab ir27.imh v1 3 62 64
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  The 'imtab' task copies an image to a column of a table.
  <P>
  Type "<TT>help tables option=sys</TT>" for a higher-level description of
  the tables package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>