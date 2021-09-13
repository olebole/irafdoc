ofixpix — Fix bad pixels using text file (proto V2.10.4)
========================================================

**Package: obsolete**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ofixpix (Jan85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>proto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ofixpix (Jan85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ofixpix</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ofixpix -- fix bad pixels using a text file (from proto V2.10.4)
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage_">USAGE	</A></H2>
  <! BeginSection: 'USAGE	'>
  <UL>
  <PRE>
  ofixpix images badpixels
  </PRE>
  </UL>
  <! EndSection:   'USAGE	'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>List of two dimensional images to be modified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_badpixels">badpixels</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='badpixels' Line='badpixels'>
  <DD>File containing the regions of bad pixels.  A region is described by
  four whitespace separated numbers consisting of the first and last columns
  of the bad region and the first and last lines of the bad region.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print the image names and the bad pixel regions?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Bad pixel regions in the list of two dimensional images are replaced by
  linear interpolation using pixels bordering the bad pixel regions.
  The bad pixel regions are input in the specified file consisting of lines
  of coordinates (x1 x2 y1 y2) where x1 and x2 are the first and last columns
  of the bad region and y1 and y2 are the first and last lines of the
  bad region.  The file may be STDIN to read from the standard input.
  The type of interpolation is determined as follows:
  <P>
  <DL>
  <DT><B><A NAME="l_">(1)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(1)'>
  <DD>If the bad region spans entire lines then the interpolation is from
  neighboring lines.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(2)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(2)'>
  <DD>If the bad region spans entire columns then the interpolation is from
  neighboring columns.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(3)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(3)'>
  <DD>If the bad region contains more lines than columns then the interpolation
  is from neighboring columns.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">(4)</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='(4)'>
  <DD>If the bad region contains the same or more columns than lines then the
  interpolation is from neighboring lines.
  </DD>
  </DL>
  <P>
  If the bad region borders the edge of the image then the interpolation
  is by replication of the first good pixel in the direction of interpolation
  and otherwise linear interpolation between the bordering lines or columns
  is used.  The verbose parameter may be used to produce of log of the pixel
  modifications.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  A detector has bad lines 10 and 25 to 27 and a partial bad column
  at column 31 between lines 35 and 50.  A bad region file is created containing
  the lines
  <P>
  <PRE>
  1 100 10 10
  1 100 25 27
  31 31 35 50
  </PRE>
  <P>
  The set of images "<TT>image*</TT>" are fixed by:
  <P>
  	cl&gt; ofixpix image* badpixfile
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_OFIXPIX">OFIXPIX V2.11</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='OFIXPIX' Line='OFIXPIX V2.11'>
  <DD>This is the V2.10.4 and earlier version of PROTO.FIXPIX.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  This is a simple minded task which can be improved by using more sophisticated
  interpolation.  The bad pixel file will eventually be replaced by image
  masks and bad pixel lists in the image.  Be careful with image sections because
  the bad pixel regions are relative to the image section.  Also if the image
  is trimmed or rotated then the bad pixel regions must be changed.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  epix, imedit, fixpix
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>