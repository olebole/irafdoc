thselect — Select tables satisfying an expression; print keywords.
==================================================================

**Package: nttools**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>thselect (Jul2000)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>ttools</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>thselect (Jul2000)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>thselect</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  thselect -- Print table keyword values.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  thselect table keywords expr
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task was based on 'hselect',
  and it behaves in a very similar manner,
  except that it works on tables rather than images.
  <P>
  Keyword values will be printed to the standard output,
  one line per input table,
  with the values separated by tabs.
  String values that contain whitespace will be enclosed in quotes.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_table">table [file name template]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='table' Line='table [file name template]'>
  <DD>A list of tables for which keywords are to be printed.
  These will be opened read-only and will not be modified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_keywords">keywords [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keywords' Line='keywords [string]'>
  <DD>One or more keywords, separated by commas and/or blanks.
  The special keywords such as "<TT>i_table</TT>"
  that are supported by 'thedit' can also be used with 'thselect'.
  <P>
  For each input table,
  the values of these keywords in the current input table will be printed,
  if 'expr' is a true expression for the current table.
  Any keyword that is not found will be silently ignored.
  <P>
  Wildcards are supported; however,
  the "<TT>@filename</TT>" syntax is not supported.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_expr">expr = "<TT>yes</TT>" [string]</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr = "yes" [string]'>
  <DD>This is a boolean expression
  to be evaluated for each table in the list.
  The default value may be used to unconditionally print keyword values.
  <P>
  The expression may include constants and/or keyword names.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Compare 'thselect' with 'thedit' for displaying a single keyword value.
  <P>
  <PRE>
      tt&gt; thselect timetag.fits[events,7] rootname yes
  <P>
      O57P03030
  <P>
      tt&gt; thedit timetag.fits[events,7] rootname .
  <P>
      timetag.fits[events,7],ROOTNAME = O57P03030 / rootname of the obser
      vation set
  </PRE>
  <P>
  2.  Compare i_file with i_table for a FITS table
  ($I and i_table are equivalent).
  <P>
  <PRE>
      tt&gt; thselect timetag.fits[events,7] i_file,i_table yes   
  <P>
      timetag.fits      timetag.fits[EVENTS,7]
  </PRE>
  <P>
  3.  Find all FITS files with DETECTOR = 'CCD' in the primary header.
  Since the primary header of a FITS file can be opened
  either as an image or as a table,
  either 'hselect' or 'thselect' could be used for this example.
  <P>
  <PRE>
      tt&gt; thselect *.fits[0] $I "detector == 'CCD'"
  <P>
      h1v11148o_1dx.fits[0]
      h4s13500o_1dx.fits[0]
      i1c1615po_1dx.fits[0]
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
  This task was written by Phil Hodge,
  based on 'hselect'.
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  hselect, thedit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'PARAMETERS' 'EXAMPLES' 'BUGS' 'REFERENCES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>