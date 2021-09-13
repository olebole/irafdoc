.. _tcopy:

tcopy — Copy tables.
====================

**Package: nttools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tcopy -- Copy tables.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tcopy intable outtable
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task is used to copy tables.  The input may be a general filename
  template, including wildcard characters or the name of a file (preceded
  by an @ sign) containing table names.  The output may be either a directory
  specification or a list of table names.  If the output is a list of tables
  then there must be the same number of names in the input and output lists,
  and the names are taken in pairs, one from input and one from output.
  The input and output tables must not be the same.
  This task will convert the format of the table
  if the output filename extension indicates it.
  For example, if the output filename extension is "<TT>.fits</TT>",
  the output table will be a fits file.
  If the output is redirected or piped,
  it will be written to a text table.
  <P>
  NOTE: Be careful when using a wildcard for the extension.
  If you have the files "<TT>table.tab</TT>" and "<TT>table.lis</TT>" in the current directory,
  for example, then the command "<TT>tcopy tab* test/</TT>" would copy both files
  to the subdirectory "<TT>test</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>intable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='intable' Line='intable [file name template]'>
  <DD>A list of one or more tables to be copied.
  </DD>
  </DL>
  <DL>
  <DT><B>outtable [file name template]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='outtable' Line='outtable [file name template]'>
  <DD>Either a directory name or a list of output table names.
  <P>
  If 'outtable' is not a directory,
  the number of input tables and output tables must be the same.
  An exception to this rule is that if 'outtable' is a FITS file
  (i.e. an existing FITS file, or the name ends in "<TT>.fits</TT>")
  then multiple input tables can be copied to one output file.
  </DD>
  </DL>
  <DL>
  <DT><B>(verbose = yes) [boolean]</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line='(verbose = yes) [boolean]'>
  <DD>Display names of input and output tables as they are copied?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To simply copy a table:
  <P>
  <PRE>
      tt&gt; tcopy table.tab tablecopy.tab
  </PRE>
  <P>
  2.  To copy one or more tables, possibly changing table type:
  <P>
  <PRE>
      tt&gt; tcopy table1.tab,table2.tab a.fits,b.tab
      tt&gt; tcopy a.fits,b.tab a.tab,b.fits
      tt&gt; tcopy a.fits &gt; a.txt
  </PRE>
  <P>
  The number of input and output tables must be the same.
  In the third case,
  "<TT>a.txt</TT>" will be a text file because
  the output table name was "<TT>STDOUT</TT>"
  (the name was implicitly set, in this case,
  because the output was redirected.)
  <P>
  3.  To copy a set of tables to a new directory:
  <P>
  <PRE>
      tt&gt; tcopy table*.tab directory
      		or
      tt&gt; tcopy table*.tab directory$
      		or
      tt&gt; tcopy table*.tab osdirectory
  </PRE>
  <P>
  where "<TT>directory</TT>" is an IRAF environment variable for a directory name,
  and "<TT>osdirectory</TT>" is an operating system directory name
  (e.g., "/user/me/"<TT> in UNIX).
  <P>
  4.  To copy only specified extensions of a FITS file:
  <P>
  <PRE>
      tt&gt; tcopy xyz.fits[3],xyz.fits[5] b.fits
  </PRE>
  <P>
  If </TT>"b.fits"<TT> did not already exist,
  it would be created and would then contain two table extensions.
  If it did already exist,
  the two extensions would be appended.
  Note that the number of input and output files are not the same;
  this is OK because the output is a FITS file
  and can therefore contain multiple table extensions.
  <P>
  5.  The input and/or output may be redirected:
  <P>
  <PRE>
      tt&gt; dir l+ | tproject columns=c7,c3 | tcopy dir.tab &gt; verbose.lis
  </PRE>
  <P>
  </TT>"verbose.lis"<TT> contains just the one line </TT>"# STDIN -&gt; dir.tab"<TT>,
  and </TT>"dir.tab"<TT> has the output of 'tproject', the file names and sizes.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  This task was written by Phil Hodge.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tdelete
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
