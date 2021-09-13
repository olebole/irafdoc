.. _mkcatalog:

mkcatalog — Type in a standard star catalog or observations file
================================================================

**Package: photcal**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkcatalog -- create or edit a catalog, usually but not necessarily
  a standard star catalog
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkcatalog catalog
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>catalog</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catalog' Line='catalog'>
  <DD>The name of the new output catalog to be created or a previously existing
  catalog to be edited.
  </DD>
  </DL>
  <DL>
  <DT><B>review = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='review' Line='review = no'>
  <DD>Review any pre-existing entries?
  </DD>
  </DL>
  <DL>
  <DT><B>verify = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>Verify each new entry?
  </DD>
  </DL>
  <DL>
  <DT><B>edit = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='edit' Line='edit = yes'>
  <DD>Enter edit mode after entering all the values?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  MKCATALOG is a script task which permits the user to create or edit
  the catalog <I>catalog</I>, usually but not necessarily, a standard star
  catalog.  MKCATALOG has two modes of operation, entry mode and edit mode.
  In entry mode MKCATALOG prompts the user for input.
  In edit mode MKCATALOG calls up the default editor specified by
  the IRAF environment variable <I>editor</I>.
  <P>
  If <I>catalog</I> is a new catalog, MKCATALOG prompts the user for 
  the name of the object id column, the names of the data columns,
  the names of the error columns (these are optional), and the widths
  of the columns. Typing the end-of-file character &lt;EOF&gt;,
  usually ^Z or ^D, terminates column definition
  and places the user in entry mode.
  In entry mode MKCATALOG prompts the user for the object ids and data values.
  Entering carriage return, &lt;CR&gt;, after MKCATALOG prompts for a new object id
  writes a blank line to the output catalog.
  Entering &lt;CR&gt; after MKCATALOG prompts for any other column
  value writes INDEF (the IRAF undefined value) in that column of the
  output catalog.
  Entry mode is terminated by typing &lt;EOF&gt; in response to a query for
  a new object id.  The user may verify each new
  entry by setting the parameter <I>verify</I> to "<TT>yes</TT>".
  <P>
  Each new catalog created by MKCATALOG has an associated format
  description file listing the column names and numbers associations defined by
  the user. This file, referenced by its parent catalog name, can be
  used as input to the MKCONFIG task.
  The actual name of the format description file on disk is constructed by
  prepending the catalog name <I>catalog</I> with the string "<TT>f</TT>" and
  appending the string "<TT>.dat</TT>". For example if a new catalog 
  called "<TT>UBVcat</TT>" is created by MKCATALOG, a format description
  file called "<TT>fUBVcat.dat</TT>" will also be created. Any pre-existing format
  description file of that name, which does not have an associated catalog
  file, will be deleted.
  <P>
  If the catalog <I>catalog</I> exists and was created with MKCATALOG,
  MKCATALOG reads
  the number of columns, the column names, and column widths from the
  header of the catalog, and enters entry mode positioned at the end
  of the file. If the parameter <I>review</I> = "<TT>yes</TT>", then the user can
  review and verify existing catalog entries before entering new ones.
  When entry mode is terminated MKCATALOG enters edit mode
  in the usual way. 
  <P>
  If <I>catalog</I> exists but was not created with MKCATALOG, MKCATALOG
  enters edit mode immediately.
  <P>
  If <I>catalog</I> is a standard star catalog, the user should be aware
  that the object ids he/she has typed in, are those against which the object
  ids in the standard star observations files will be matched by the
  fitting task FITPARAMS.
  Normally the user is expected to edit the object ids in the standard
  star observations
  files to match those in the standard star catalog.
  For example, the PHOTCAL APPHOT/DAOPHOT pre-processor tasks MKNOBSFILE
  and MKOBSFILE, produce observations files whose object ids
  are of the form "<TT>field-#</TT>", where "<TT>field</TT>" is the name
  of the observed field and "<TT>#</TT>" is a sequence number, which is defined
  only if there is more than one observed star in the field.
  In this scheme the id of the  the fourth observed star in the field "<TT>M92</TT>"
  is "<TT>M92-4</TT>". If this star is actually the standard star "<TT>IX-10</TT>" in
  <I>catalog</I>, the user must change the object id in the observations file
  to "<TT>IX-10</TT>". Alternatively the user can set up the naming
  convention in <I>catalog</I> itself, to match  the naming
  convention of MKNOBSFILE
  or MKOBSFILE by assigning the standard stars names like "<TT>field-#</TT>" and
  subsequently measuring the standard stars in the same order as they
  appear in the catalog.  In this scheme star, "<TT>M92-4</TT>" in
  the observations file would also be "<TT>M92-4</TT>" in the standard star 
  catalog, and no editing would be required. This technique is most useful
  for standard sequences in clusters.
  <P>
  THE MKCATALOG TASK AND THE ENTIRE PHOTCAL PACKAGE IMPOSE THE FOLLOWING
  RESTRICTIONS
  ON BOTH STAR ID NAMES AND THE COLUMN ID NAMES THAT MAY BE ASSIGNED, AND ON
  THE FORMAT OF EACH FIELD.
  <P>
  Object id names must be composed of characters in the set [a-z,A-Z,0-9,+,-,_].
  Other characters may be included as part of the user id, but 
  will be ignored by the PHOTCAL id matching code. Object id names are
  case insensitive. To the id matching code the name "<TT>BD+61_305</TT>" is the
  same as "<TT>bd+61_305</TT>".
  <P>
  Column names must be composed of characters in the set [a-z,A-Z,0-9]
  and the first character of the column name must be a letter of the alphabet.
  This means for example, that an individual column cannot be assigned the
  name "<TT>B-V</TT>", since "<TT>B-V</TT>" will be interpreted as an arithmetic expression not
  as a variable, by the PHOTCAL equation parsing routines.
  "<TT>B-V</TT>" may be replaced with something like "<TT>BV</TT>" or "<TT>BMV</TT>".
  MKCATALOG will complain if the user tries to enter an illegal column name.
  Column names are case sensitive. Column "<TT>BV</TT>" is not the same as 
  column "<TT>bv</TT>".
  <P>
  Whitespace  is not permitted in either the object ids or in the column
  values. MKCATALOG will truncate any id or column value at the first
  whitespace encountered. The column widths entered by the user are used
  solely to determine
  the maximum width of each field (excess characters will be truncated)
  and to align the columns for ease of
  visual inspection by the user. The column widths are not used by the 
  PHOTCAL catalog reading code.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Create a new standard star catalog containing the 3 photometric indices
  V, B-V, and U-B and their respective errors. Note that MKCATALOG supplies
  default names of the form "<TT>error(name)</TT>" for the error columns where "<TT>name</TT>"
  is the name of the previous column. Users are strongly urged to use the
  default names since they simplify the use of the statistical weighting
  scheme in the FITPARAMS task. If no error information is available
  error column entry can be skipped by typing &lt;-&gt; in response to the query
  for an error column name.
  <P>
  <PRE>
  ph&gt; mkcatalog UBVcat
  <P>
      and shown below, note that the end-of-file character &lt;EOF&gt; is
      actually ^Z in this case
  <P>
  Enter the id column name (name, &lt;CR&gt;=ID, &lt;EOF&gt;=quit entry): 
      Enter width of id column (width, &lt;CR&gt;=15): 
  Enter a name for column 2 (name, &lt;CR&gt;=COL2, &lt;EOF&gt;=quit entry): V
      Enter width of column 2 (width, &lt;CR&gt;=10): 
  Enter a name for error column 3 (name, &lt;CR&gt;=error(V), &lt;-&gt;=skip): 
      Enter width of column 3 (width, &lt;CR&gt;=10): 
  Enter a name for column 4 (name, &lt;CR&gt;=COL4, &lt;EOF&gt;=quit entry): BV
      Enter width of column 4 (width, &lt;CR&gt;=10): 
  Enter a name for error column 5 (name, &lt;CR&gt;=error(BV), &lt;-&gt;=skip): 
      Enter width of column 5 (width, &lt;CR&gt;=10): 
  Enter a name for column 6 (name, &lt;CR&gt;=COL6, &lt;EOF&gt;=quit entry): UB
      Enter width of column 6 (width, &lt;CR&gt;=10): 
  Enter a name for error column 7 (name, &lt;CR&gt;=error(UB), &lt;-&gt;=skip): 
      Enter width of column 7 (width, &lt;CR&gt;=10): 
  Enter a name for column 8 (name, &lt;CR&gt;=COL8, &lt;EOF&gt;=quit entry): ^Z
  <P>
  <P>
  Catalog UBVcat in file UBVcat has 7 columns
  	Column 1:  ID             
  	Column 2:  V         
  	Column 3:  error(V)  
  	Column 4:  BV        
  	Column 5:  error(BV) 
  	Column 6:  UB        
  	Column 7:  error(UB) 
  <P>
  <P>
  <P>
  <P>
  <P>
  </PRE>
  <P>
  <P>
  2. Add new entries to the file created in example 1.
  <P>
  <PRE>
  ph&gt; mkcatalog UBVcat
  <P>
  <P>
  <P>
  </PRE>
  <P>
  <P>
  3. Edit an existing catalog created with a foreign program.
  <P>
  <PRE>
  ph&gt; mkcatalog VRI.usr
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  The longest line permitted by an editor varies from editor to
  editor. Users should be aware that it may not be possible to use
  edit mode on very long text lines.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  photcal$catalogs/README,mknobsfile,mkobsfile,mkconfig
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
