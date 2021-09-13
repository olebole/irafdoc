subsets — Subtract pairs in strings of spectra
==============================================

**Package: iids**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>subsets (Jun87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.ccdred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>subsets (Jun87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>subsets</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  subsets -- Description of CCD subsets
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <B>ccdred</B> package groups observation into subsets.
  The image header parameter used to identify the subsets is defined
  in the instrument translation file (see help for <B>instruments</B>).
  For example to select subsets by the header parameter "<TT>filters</TT>" the
  instrument translation file would contain the line:
  <P>
  	subset	filters
  <P>
  Observations are generally grouped into subsets based on a common
  instrument configuration such as a filter, aperture mask,
  grating setting, etc.  This allows combining images from several
  different subsets automatically and applying the appropriate
  flat field image when processing the observations.  For example
  if the subsets are by filter then <B>flatcombine</B> will search
  through all the images, find the flat field images (based on the
  CCD type parameter), and combine the flat field images from
  each filter separately.  Then when processing the images the
  flat field with the same filter as the observation is used.
  <P>
  Each subset is assigned a short identifier.  This is listed when
  using <B>ccdlist</B> and is appended to a root name when combining
  images.  Because the subset parameter in the image header may be
  any string there must be a mapping applied to generate unique
  identifiers.  This mapping is defined in the file given by
  the package parameter <I>ccdred.ssfile</I>.  The file consists of
  lines with two fields (except that comment lines may be included
  as a line by itself or following the second field):
  <P>
  	'subset string'	subset_id
  <P>
  where the subset string is the image header string and the subset_id is
  the identifier.  A field must be quoted if it contains blanks.  The
  user may create this file but generally it is created by the tasks.  The
  tasks use the first word of the subset string as the default identifier
  and a number is appended if the first word is not unique.  The
  following steps define the subset identifier:
  <P>
  <DL>
  <DT><B><A NAME="l_">(1)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(1)'>
  <DD>Search the subset file, if present, for a matching subset string and
  use the defined subset identifier.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(2)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(2)'>
  <DD>If there is no matching subset string use the first word of the
  image header subset string and, if it is not unique,
  add successive integers until it is unique.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(3)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(3)'>
  <DD>If the identifier is not in the subset file create the file and add an
  entry if necessary.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The subset file is "<TT>subsets</TT>" (the default).  The subset parameter is
  translated to "<TT>f1pos</TT>" in the image header (the old NOAO CCD parameter)
  which is an integer filter position.  After running a task, say
  "<TT>ccdlist *.imh</TT>" to cause all filters to be checked, the subset file contains:
  <P>
  <PRE>
  	<TT>'2'</TT>	2
  	<TT>'5'</TT>	5
  	<TT>'3'</TT>	3
  </PRE>
  <P>
  The order reflects the order in which the filters were encountered.
  Suppose the user wants to have more descriptive names then the subset
  file can be created or edited to the form:
  <P>
  <PRE>
  	# Sample translation file.
  	<TT>'2'</TT>	U
  	<TT>'3'</TT>	B
  	<TT>'4'</TT>	V
  </PRE>
  <P>
  (This is only an example and does not mean these are standard filters.)
  <P>
  2. As another example suppose the image header parameter is "<TT>filter</TT>" and
  contains more descriptive strings.  The subset file might become:
  <P>
  <PRE>
  	'GG 385 Filter'	GG
  	'GG 495 Filter'	GG1
  	'RG 610 Filter'	RG
  	'H-ALPHA'	H_ALPHA
  </PRE>
  <P>
  In this case use of the first word was not very good but it is unique.
  It is better if the filters are encoded with the thought that the first
  word will be used by <B>ccdred</B>; it should be short and unique.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  instruments
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>