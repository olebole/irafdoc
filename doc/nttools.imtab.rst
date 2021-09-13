imtab — Copy an image to a table column.
========================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>imtab (Mar2000)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>imtab (Mar2000)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>imtab</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  imtab -- Create a table from an image.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  imtab input outtable colname
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task copies data from an image to a table.
  Pixel values are read from the image line by line
  and written to a column in increasing row number.
  The image may be of any dimension,
  but a single column is written.
  If the table already exists then columns will be added to it;
  names of new columns must not conflict with existing names.
  If the table does not exist it will be created.
  <P>
  The number of names in the 'input' list must be the same as
  the number of names in the 'outtable' list,
  unless 'outtable' is "<TT>STDOUT</TT>".
  <P>
  Information about the image dimension and axis lengths will not be kept
  in keywords, but there is an option to write the image pixel numbers
  to columns of the table.
  The pixel coordinates may be just the pixel numbers,
  or they may be world coordinates at the pixel locations.
  <P>
  A history record will be added to the table giving
  the name of the data column and the name of the image.
  If pixel coordinates are written to the table,
  another history record is written that also gives
  the column name for the image data
  and gives the column names for the pixel coordinates.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input = "<TT></TT>" [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input = "" [file name template]'>
  <DD>The names of the images to be written to the tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable = "<TT></TT>" [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable = "" [file name template]'>
  <DD>The names of the output tables.
  If outtable = "<TT>STDOUT</TT>" or if the output has been redirected,
  the values will be written to the standard output.
  <P>
  If the output table is of type text (e.g. STDOUT),
  the data values will be in the first column.
  If the pixel coordinates are also printed,
  they will be in the following columns.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_colname">colname = "<TT></TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='colname' Line='colname = "" [string]'>
  <DD>A column of this name will be created in the output table,
  and the values of the image will be written to this column.
  The same column name will be used for all output tables.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(pname = "<TT></TT>") [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(pname = "") [string]'>
  <DD>If 'pname' is not null,
  the pixel coordinates will also be written to columns of the table.
  The names of these columns will be the value of 'pname' with the
  numbers 1, 2, 3, etc appended,
  corresponding to the sample number, line number, band number, etc.
  This may be especially useful for a multi-dimensional input image,
  since all the data values are written to one column.
  The same column names will be used for all output tables.
  See also 'wcs' and 'formats'.
  <P>
  If 'pname' is null (or blank) the pixel numbers will not be written.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(wcs = "<TT>logical</TT>") [string, allowed values:  logical | physical | world]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(wcs = "logical") [string, allowed values:  logical | physical | world]'>
  <DD>This parameter is only gotten if 'pname' is not null.
  In this case, the user has the option of which coordinate system
  should be used when writing pixel coordinates to the table.
  The "<TT>logical</TT>" coordinates are simply the pixel numbers
  of the image or image section.
  The "<TT>physical</TT>" coordinates are also pixel numbers,
  but they can differ from logical coordinates
  if an image section has been taken.
  Physical coordinates have the same origin and sampling as the original image.
  The "<TT>world</TT>" coordinates are coordinates such as wavelength, time,
  or right ascension and declination.
  The translation from logical to world coordinates is given by
  header keywords CRVAL1, CRPIX1, CD1_1, CTYPE1, etc.
  <P>
  The number of pixel coordinates written by 'imtab' differs from
  the number written by 'listpixels' when wcs = "<TT>physical</TT>" or "<TT>world</TT>"
  and an image section was used that reduces the dimension of the image.
  'imtab' gives one pixel coordinate column for each dimension
  of the original image, while 'listpixels' gives one pixel coordinate
  for each dimension of the image section.
  <P>
  Type "<TT>help mwcs$MWCS.hlp fi+</TT>" for extensive information on coordinate systems.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(formats) [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(formats) [string]'>
  <DD>The print formats to use for the pixel coordinates, one format
  per axis, with the individual formats separated by whitespace.
  This parameter is only gotten if 'pname' is not null.
  If the formats are not given, a default format is assigned.
  See the help for 'listpixels' for extensive information on formats.
  These formats are saved in the descriptors for the table columns,
  so these formats will be used if the table is printed.
  If the output table is text rather than binary,
  these formats will be used to write the coordinates to the text table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(tbltype = "<TT>default</TT>") [string, allowed values: default | row |</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(tbltype = "default") [string, allowed values: default | row |'>
  <DD>column | text ]
  <P>
  If the output table does not already exist,
  you can specify whether the table should be created in row or column
  ordered format.
  As an alternative to a binary table,
  tbltype = "<TT>text</TT>" means the output will be a plain text file.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Copy image "<TT>hr465_flux.imh</TT>" to table "<TT>hr465.tab</TT>", column "<TT>flux</TT>":
  <P>
  <PRE>
  	tt&gt; imtab hr465_flux.imh hr465.tab flux
  </PRE>
  <P>
  2.  Copy the 2-D image "<TT>ir27.hhh</TT>" to column "<TT>ir27</TT>" of table "<TT>map.tab</TT>",
  saving the pixel numbers in columns "<TT>pix1</TT>" and "<TT>pix2</TT>":
  <P>
  <PRE>
  	tt&gt; imtab ir27.hhh map.tab ir27 pname="pix"
  </PRE>
  <P>
  3.  Copy the 1-D section [257:257,129:384] of
  x0y70206t.d0h to column "<TT>x0y70206</TT>" of table "<TT>focus.tab</TT>".
  Also write the right ascension and declination
  ("<TT>world</TT>" coordinates) to columns "<TT>p1</TT>" and "<TT>p2</TT>" respectively
  using HH:MM:SS.d and DD:MM:SS.d formats.
  We use "<TT>%12.1H</TT>" for right ascension and "<TT>%12.1h</TT>" for declination.
  The capital "<TT>H</TT>" in the format means that the values will be divided by 15
  to convert from degrees to hours before formatting in sexagesimal.
  Note that we get two columns of pixel coordinates even though
  the image section is only 1-D.
  Physical or world coordinates will be 2-D in this case
  because the original image "<TT>x0y70206t.d0h</TT>" is 2-D.
  <P>
  <PRE>
  	tt&gt; imtab x0y70206t.d0h[257:257,129:384] focus.tab x0y70206 \<BR>
  	&gt;&gt;&gt; pname="p" wcs="world" formats="%12.1H %12.1h"
  </PRE>
  <P>
  4.  Use the same image as in the previous example,
  but print the values on the standard output.
  <P>
  <PRE>
  	tt&gt; imtab x0y70206t.d0h[257:257,129:384] STDOUT x0y70206 \<BR>
  	&gt;&gt;&gt; pname="p" wcs="world" formats="%12.1H %12.1h"
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
  The 'tabim' task copies a column of a table to an image.
  The 'listpixels' task in the 'images' package writes data values and
  pixel coordinates to the standard output.
  The parameters 'wcs' and 'formats' are the same in 'imtab' and 'listpixels'.
  For detailed information on the distinction between logical, physical and
  world coordinates, type "<TT>help mwcs$MWCS.hlp fi+</TT>".
  <P>
  Type "<TT>help tables option=sys</TT>" for a higher-level description of
  the tables package.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>