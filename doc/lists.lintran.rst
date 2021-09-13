lintran — Perform linear transformation of a list
=================================================

**Package: lists**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>lintran (Apr84)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>lists</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>lintran (Apr84)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>lintran</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  lintran -- perform a linear transformation of a list
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  lintran files
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>List file or files to be transformed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xfield">xfield = 1, yfield = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xfield' Line='xfield = 1, yfield = 2'>
  <DD>Fields containing the x and y coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_x1">x1 = 0.0, y1 = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x1' Line='x1 = 0.0, y1 = 0.0'>
  <DD>Coordinates of current origin.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xscale">xscale = 1.0, yscale = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xscale' Line='xscale = 1.0, yscale = 1.0'>
  <DD>Scale factor to be applied to the input coordinates, relative
  to the current origin [x1,y1].
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_angle">angle = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='angle' Line='angle = 0.0'>
  <DD>Rotation angle about the origin [x1,y1].  This angle, measured
  counter clockwise from the positive x axis, is entered in
  degrees, unless <B>radians</B> = yes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_x2">x2 = 0.0, y2 = 0.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x2' Line='x2 = 0.0, y2 = 0.0'>
  <DD>Coordinates of the new origin; input coordinates are shifted by an 
  amount (x2-x1) and (y2-y1).  Positive shifts indicate increasing distance
  from the current origin.  Applied after scaling and rotating the input 
  coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_radians">radians = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='radians' Line='radians = no'>
  <DD>If this parameter is set to yes, <B>angle</B> is input
  in radians, not degrees.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_min_sigdigits">min_sigdigits = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='min_sigdigits' Line='min_sigdigits = 1'>
  <DD>The number of significant digits to be output in the transformed fields 
  is the maximum of this parameter and the number of input significant digits. 
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Specified fields from the input list can be scaled, rotated and shifted.
  Two fields of each input line are designated
  as the x and y coordinates to be transformed (default: fields 1, 2).
  All other fields are be preserved across the transformation.  
  For clarification, the equations used in the transformation are shown below:
  <P>
  <PRE>
  <PRE>
  	1. Subtract off the current origin:
      
      	xt = x - x1
      	yt = y - y1
  <P>
  	2. Scale and rotate the coordinates:
      
  	xs = xt * xscale
  	ys = yt * yscale
      	xt = xs * cos(angle) - ys * sin(angle)
      	yt = xs * sin(angle) + ys * cos(angle)
  <P>
  	3. Shift to the new origin:
  <P>
  	xt = xt + x2
  	yt = yt + y2
  </PRE>
  </PRE>
  <P>
  Comment lines and blank lines are passed on to the output unmodified
  (a comment line is any line beginning with the character <TT>'#'</TT>).
  If either x or y is indefinite
  and no rotation is being performed, the corresponding
  output coordinate will be indefinite.  If either input coordinate is indefinite
  and a rotation is being performed, both output coordinates will be indefinite.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Shift the coordinate list frame1 so it represents positions
  in a second exposure of a star field, not registered with the first.  Take
  the coordinates of a star in frame1 to be the current origin 
  (e.g., [35.7, 389.2]); the new origin is then the coordinates of the same
  star in the second exposure ([36.9, 400.0]).  The shifted list is saved in
  file "<TT>frame2</TT>":
  <P>
      cl&gt; lintran frame1 x1=35.7 y1=389.2 x2=36.9 y2=400.0 &gt; frame2
  <P>
  2. Apply a shift of +3.4 units in x, -1.3 units in y to the input list
  read from the standard input, writing the output list on the standard
  output.  
  <P>
      cl&gt; list_stream | lintran x2=3.4 y2=-1.3
  <P>
  3. Rotate a coordinate list of a 800x800 frame by 90 degrees.  The
  rotated coordinate list would represent positions in the field if it had
  been rotated, for example, from East to the right to East to the top.  
  Note that the rotation takes place about the central pixel [400.50,400.50]
  and that the current and new origins are the same:
  <P>
      cl&gt; lintran picture x1=400.5 y1=400.5 x2=400.5 y2=400.5 angle=90
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>