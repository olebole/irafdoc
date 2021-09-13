tiimage — Insert images into rows of a 3-D table.
=================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>tiimage (Jan97)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>tables</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>tiimage (Jan97)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>tiimage</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  tiimage -- Inserts images into rows of a 3-D table.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  tiimage input outtable
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task performs the inverse operation of task tximage: it inserts one or 
  more images into rows of a 3-D table  The input may be a filename template, 
  including wildcard characters, or the name of a file (preceded by an @ sign) 
  containing image names.  The output is a single 3-D table name.
  Each image in the input list is inserted as an array into a single cell at 
  the specified row in the output table. Any dimensionality information existent
  in the input image is lost in the process, that is, the image will be always
  inserted as a 1-D array, regardless of its number of axis.
  <P>
  If the output table exists, insertion will be done in place. Alternatively, 
  the task can create a 3-D table from information taken either from a template 
  3-D table, or, if this table is not supplied, from the input images themselves. 
  This task supports a column selector in table names. This selector may be 
  used to select a single column in the table. If no selector is used, all 
  columns will be processed. Type 'help selectors' to see a description of 
  the selector syntax. 
  <P>
  If the output table exists, insertion may take place in two ways. If the
  output table name contains a column selector that selects a single column
  in the table, all input images will be inserted in that column, starting
  at the row pointed by task parameter "<TT>row</TT>". 
  If "<TT>row</TT>" is negative or INDEF the task will look for the ORIG_ROW
  keyword in the image header and use that keyword value for row number.
  The second mode of insertion in an existing table is used if no matching
  column selector is found in the output table name. In this case the task
  will look for the columnar information written in the input image header by 
  task tximage, and use that information to place the image in the proper 
  column. If no columnar information exists in the header, or if the column 
  name in there does not match any column in the output table, the image is 
  skipped and the user warned. The "<TT>row</TT>" parameter processing works the same 
  way in this second mode.
  <P>
  If the output table does not exist, the task will look for a template table
  where to take column information from. If the template exists, the insertion
  operation will be performed in an analogous way as above. Notice that the
  result may be a single-column table if the template has a valid (matching)
  column selector in its name, or a sparse table if not, because only the 
  actual input images will be stored in an otherwise empty table (the template 
  data is not copied into the output, only the column descriptors).
  <P>
  If the template is missing, the task will attempt to retrieve columnar
  information from the input image headers and build the output table with
  enough columns and rows to fit all images in the list. Only images that
  have columnar information in their headers can be processed, though. If
  no images are found with the proper header keywords, no output takes place.
  <P>
  NOTE: Both the output and template table names must always be supplied 
  complete, including their extension. Otherwise the task may get confused 
  on the existence of an already existing table.
  <P>
  The column matching criterion is based on the column name. An error results 
  when data types in input image and output column do not agree.
  <P>
  If the maximum array size in a target column in the output 3-D table is
  larger than the number of pixels in the input image, the array will be filled 
  up starting from its first element, and the empty elements at the end will 
  be set to INDEF. If the maximum array size is smaller than the number of 
  pixels, insertion begins by the first pixel up to the maximum allowable size, 
  the remaining pixels being ignored.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input [image name list/template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input [image name list/template]'>
  <DD>A list of one or more images to be inserted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_outtable">outtable [table name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [table name]'>
  <DD>Name of 3-D output table, including extension. No support exists for 
  "<TT>STDOUT</TT>" (ASCII output).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(template = "<TT></TT>") [table name]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(template = "") [table name]'>
  <DD>Name of 3-D table to be used as template when creating a new output table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(row = INDEF) [int]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(row = INDEF) [int]'>
  <DD>Row where insertion begins. If set to INDEF or a negative value, the row
  number will be looked for in the input image header.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(verbose = yes) [boolean]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]'>
  <DD>Display names as files are processed ?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Insert images into a 3-D table at column named FLUX:
  <P>
  <PRE>
  cl&gt; tiimage flux*.hhh "otable.tab[c:FLUX]"
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  The output and template table names must be supplied in full, including 
  the extension (e.g. "<TT>.tab</TT>"). If the output table name is not typed in full, 
  the task will create a new table in place of the existing one, with only 
  the rows actually inserted. This behavior relates to the way the underlying 
  "<TT>access</TT>" routine in IRAF's fio library works.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by I. Busko.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tximage, selectors
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>