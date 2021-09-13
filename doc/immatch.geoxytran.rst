geoxytran — Transform coordinate lists using the geomap transforms
==================================================================

**Package: immatch**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>geoxytran (Apr95)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.immatch</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>geoxytran (Apr95)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>geoxytran</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  geoxytran -- geometrically transform a list of coordinates
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  geoxytran input output database transforms
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input coordinate files to be transformed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The list of output transformed coordinate files. The number of output files must
  be one or equal to the number of input files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The name of the text database file written by the geomap task which
  contains the desired spatial transformation.
  If database is undefined geoxytran computes
  a linear transformation using the current
  values of the xref, yref, xout, yout, xshift, yshift, xmag, ymag, xrotation,
  and yrotation parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_transforms">transforms</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transforms' Line='transforms'>
  <DD>The database record containing the desired spatial transformation. 
  The number of records must be one or equal to the number of input coordinate
  files. Transforms is usually the name of the coordinate file that the
  geomap task used to compute the spatial transformation.
  If defined the values of xref, yref, xout, yout, xshift, yshift, xmag, ymag,
  xrotation, and yrotation will supersede the computed values in the
  database file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_geometry">geometry = "<TT>geometric</TT>" (linear|geometric)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='geometry' Line='geometry = "geometric" (linear|geometric)'>
  <DD>The type of geometric transformation. The geometry parameter is
  only requested if database is defined. The options are:
  <DL>
  <DT><B><A NAME="l_linear">linear</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Perform only the linear part of the spatial transformation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_geometric">geometric</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='geometric' Line='geometric'>
  <DD>Compute both the linear and distortion portions of the spatial transformation.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_direction">direction = "<TT>forward</TT>" (forward|backward)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='direction' Line='direction = "forward" (forward|backward)'>
  <DD>The transformation direction may be "<TT>forward</TT>" or "<TT>backward</TT>".  The forward
  direction directly evaluates the database solution.  The backward
  direction iteratively determines the coordinate which evaluates to the
  specified coordinate.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xref">xref = INDEF, yref = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xref' Line='xref = INDEF, yref = INDEF'>
  <DD>The x and y coordinates of the reference origin.
  If the database file is undefined xref and
  yref  default to [0.0,0.0]. Otherwise xref and yref
  default to the mean of minimum and maximum x and y values
  [(xmin + xmax) / 2.0, (ymin + ymax) / 2.0] computed by geomap.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmag">xmag = INDEF, ymag = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag = INDEF, ymag = INDEF'>
  <DD>The x and y scale factors in input units
  per reference unit. If database is undefined xmag and ymag
  default to [1.0, 1.0]. Otherwise xmag and ymag default to the values computed
  by geomap. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xrotation">xrotation = INDEF, yrotation = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xrotation' Line='xrotation = INDEF, yrotation = INDEF'>
  <DD>The x and y rotation angles in degrees measured counter-clockwise with
  respect to the x and y axes. If database
  is undefined then xrotation and yrotation are interpreted as the
  rotation of the coordinates with respect to the x and y axes and
  default to [0.0, 0.0]. For example xrotation and yrotation values of
  [30.0, 30.0] will rotate a point 30 counter-clockwise with respect
  to the x and y axes.  Otherwise xrotation and yrotation default to the
  values computed by geomap. Geomap computes the x and y rotation angles
  of the x and y axes, not the rotation angle of the coordinates. An output
  coordinate system rotated 30 degrees counter-clockwise with respect
  to the reference coordinate system will produce xrotation and yrotation
  values of [330.0,330.0] or equivalently [-30.0,-30.0] in the database file
  not [30.0,30.0].
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xout">xout = INDEF, yout = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xout' Line='xout = INDEF, yout = INDEF'>
  <DD>The x and y coordinates of the output origin.
  If the database file is undefined xout and
  yout  default to [0.0,0.0].
  If database is defined xout and yout
  default to the position that the reference origin [xref,yref]
  occupies in the transformed system.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xshift">xshift = INDEF, yshift = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xshift' Line='xshift = INDEF, yshift = INDEF'>
  <DD>The x and y shift of the reference origin in output units.
  If the database file is undefined xshift and yshift default to [0.0,0.0].
  If the database file is defined xshift and yshift default to the
  values computed by geomap. If defined xshift and yshift take precedence over
  the x and y shifts determined from xref, yref, xout and yout.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xcolumn">xcolumn = 1, ycolumn = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcolumn' Line='xcolumn = 1, ycolumn = 2'>
  <DD>The columns in the input coordinate file containing the x and y coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_calctype">calctype = "<TT>real</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calctype' Line='calctype = "real"'>
  <DD>The precision of the coordinate transformation calculations. The options
  are "<TT>real</TT>" and "<TT>double</TT>".  Note that this only applies to a "<TT>forward</TT>"
  transformation.  The "<TT>backward</TT>" transformation is done iteratively and
  is always calculated in double precision to get the best convergence.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xformat">xformat = "<TT></TT>", yformat = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xformat' Line='xformat = "", yformat = ""'>
  <DD>The default output format for the computed x and y coordinates. If
  xformat and yformat are undefined geoxytran outputs the coordinates
  using the maximum of the precision of the input coordinates
  and the value of the <I>min_sigdigits</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_min_sigdigits">min_sigdigits = 7</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='min_sigdigits' Line='min_sigdigits = 7'>
  <DD>The minimum precision of the output x and y coordinates.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  GEOXYTRAN applies  a coordinate transformation to a list of reference
  coordinates in the text file <I>input</I> and writes the transformed
  coordinates to the text file <I>output</I>. The input  coordinates
  are read from, and the output coordinates written to, columns
  <I>xcolumn</I> and <I>ycolumn</I> in the input and output
  files. The format of the output coordinates can be specified using the
  <I>xformat</I> and <I>yformat</I> parameters. If the output formats
  are unspecified the coordinates are written out with a precision
  which is the maximum of the precision of the input coordinates
  and the value of the <I>min_sigdigits</I> parameter. All remaining fields in
  the input file are copied to the output file without modification.
  Blank lines and comment lines are also passed to the output file
  unaltered.
  <P>
  The coordinate transformation either be read from record <I>transforms</I>
  in the database file <I>database</I> computed by GEOMAP, or specified
  by the user via the <I>xref</I>, <I>yref</I>, <I>xmag</I>, <I>ymag</I>,
  <I>xrotation</I>, <I>yrotation</I>, <I>xout</I>, <I>yout</I>, <I>xshift</I>,
  and <I>yshift</I> parameters.
  <P>
  The transformation computed by GEOMAP has the following form.
  <P>
  <PRE>
  	xout = f (xref, yref)
  	yout = g (xref, yref)
  </PRE>
  <P>
  The functions f and g are either a power series polynomial or a Legendre
  or Chebyshev polynomial surface whose order and region of validity were
  set by the user when GEOMAP was run. The computed transformation is
  arbitrary and does not correspond to any physically meaningful model.
  However the first order terms can be given the simple geometrical
  interpretation shown below.
  <P>
  <PRE>
  	xout = a + b * xref + c * yref
  	yout = d + e * xref + f * yref
  	   b = xmag * cos (xrotation)
  	   c = ymag * sin (yrotation)
  	   e = -xmag * sin (xrotation)
  	   f = ymag * cos (yrotation)
  	   a = x0 - b * xref0 - c * yref0 = xshift
  	   d = y0 - e * xref0 - f * yref0 = xshift
  </PRE>
  <P>
  Xref0, yref0, x0, and
  y0 are the origins of the reference and output coordinate systems
  respectively. xmag and ymag are the x and y scale factors in output units
  per reference unit and xrotation and yrotation are the rotation angles measured
  counter-clockwise of the x and y axes.
  <P>
  The linear portion of the GEOMAP transformation may be altered after the fact
  by setting some or all of the parameters <I>xref</I>, <I>yref</I>, <I>xout</I>,
  <I>yout</I>, <I>xshift</I>, <I>yshift</I>, <I>xmag</I>, <I>ymag</I>, <I>xrotation</I>,
  and <I>yrotation</I>. If defined these parameters will replace the corresponding
  values in the GEOMAP database file.
  Xref, yref, xshift, yshift, xout and yout can be used to redefine the shift
  where xshift and yshift take precedence over xref, yref, xout and yout.
  Xmag, and ymag can be used to reset the scale of the transformation.
  Xrotation and yrotation can be used to redefine the orientation of the
  transformation. Note that xrotation and yrotation are interpreted as
  the rotation of the coordinate axes not the coordinates.
  The default values of these parameters are.
  <P>
  <PRE>
  	  xref = (xmin + xmax) / 2.0
  	  yref = (ymin + ymax) / 2.0
  	  xout = f (xref,yref)
  	  yout = g (xref,yref)
  	xshift = xshift (database) = xout - f(xref,yref)
  	yshift = yshift (database) = yout - g(xref,yref)
  	  xmag = xmag (database)
  	  ymag = ymag (database)
       xrotation = xrotation (database)
       yrotation = yrotation (database)
  </PRE>
  <P>
  If the GEOMAP database is undefined then GEOXYTRAN performs a linear
  transformation on the input coordinates using the parameters
  <I>xref</I>, <I>yref</I>, <I>xmag</I>, <I>ymag</I>, <I>xrotation</I>,
  <I>yrotation</I>, <I>xout</I>, <I>yout</I>, <I>xshift</I>, and
  <I>yshift</I> as shown below. Note that in this case xrotation and
  yrotation are interpreted as the rotation of the coordinates
  themselves not the coordinate axes.
  <P>
  <PRE>
  	xout = a + b * xref + c * yref
  	yout = d + e * xref + f * yref
  	   b = xmag * cos (xrotation)
  	   c = -ymag * sin (yrotation)
  	   e = xmag * sin (xrotation)
  	   f = ymag * cos (yrotation)
  	   a = xo - b * xref0 - c * yref0 = xshift
  	   d = yo - e * xref0 - f * yref0 = xshift
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_forward_vs__backward_transformations">Forward vs. Backward Transformations</A></H2>
  <! BeginSection: 'Forward vs. Backward Transformations'>
  <UL>
  <P>
  The transformation direction is specified by the <I>direction</I> parameter
  which may take the values "<TT>forward</TT>" or "<TT>backward</TT>".  The forward transformation
  is a direct evaluation of the database solution.  The backward
  transformation is an iterative evaluation to obtain the coordinate which
  evaluates to the desired coordinate.
  <P>
  When the same solution is used with <B>geotran</B> to transform an image
  to another image matching the "<TT>reference</TT>" image is needed to obtain
  coordinates in the transformed image.  This is because the transformation
  is produced with <B>geomap</B> to map "<TT>reference</TT>" coordinates to the
  image which is subsequently transformed.  Therefore, if you have coordinates
  in the image which has been transformed then you should use the "<TT>backward</TT>"
  transformation to get coordinates for the transformed image.  But if you
  have standard coordinates from the reference image being matched then you
  would use the "<TT>forward</TT>" transformation.  If you are not sure then you can
  use <B>tvmark</B> to overlay the results to find which direction produces
  the desired coordinates.
  <P>
  Because the backward transformation is performed iteratively it can be
  slow.  If higher speeds are desired, such as when evaluating a very
  large number of coordinates, one might create a transformation solution
  that can be evaluated in the forward direction.  This is done by
  using <B>geomap</B> with the reference and target coordinates reversed.
  <P>
  </UL>
  <! EndSection:   'Forward vs. Backward Transformations'>
  <H2><A NAME="s_formats">FORMATS</A></H2>
  <! BeginSection: 'FORMATS'>
  <UL>
  <P>
  A  format  specification has the form "<TT>%w.dCn</TT>", where w is the field
  width, d is the number of decimal places or the number of digits  of
  precision,  C  is  the  format  code,  and  n is radix character for
  format code "<TT>r</TT>" only.  The w and d fields are optional.  The  format
  codes C are as follows:
     
  <PRE>
  b       boolean (YES or NO)
  c       single character (c or '\c' or '\0nnn')
  d       decimal integer
  e       exponential format (D specifies the precision)
  f       fixed format (D specifies the number of decimal places)
  g       general format (D specifies the precision)
  h       hms format (hh:mm:ss.ss, D = no. decimal places)
  m       minutes, seconds (or hours, minutes) (mm:ss.ss)
  o       octal integer
  rN      convert integer in any radix N
  s       string (D field specifies max chars to print)
  t       advance To column given as field W
  u       unsigned decimal integer
  w       output the number of spaces given by field W
  x       hexadecimal integer
  z       complex format (r,r) (D = precision)
     
     
  Conventions for w (field width) specification:
     
      W =  n      right justify in field of N characters, blank fill
          -n      left justify in field of N characters, blank fill
          0n      zero fill at left (only if right justified)
  absent, 0       use as much space as needed (D field sets precision)
     
  Escape sequences (e.g. "\n" for newline):
     
  \b      backspace   (not implemented)
       formfeed
  \n      newline (crlf)
  \r      carriage return
  \t      tab
  \"      string delimiter character
  \'      character constant delimiter character
  \\      backslash character
  \nnn    octal value of character
     
  Examples
     
  %s          format a string using as much space as required
  %-10s       left justify a string in a field of 10 characters
  %-10.10s    left justify and truncate a string in a field of 10 characters
  %10s        right justify a string in a field of 10 characters
  %10.10s     right justify and truncate a string in a field of 10 characters
     
  %7.3f       print a real number right justified in floating point format
  %-7.3f      same as above but left justified
  %15.7e      print a real number right justified in exponential format
  %-15.7e     same as above but left justified
  %12.5g      print a real number right justified in general format
  %-12.5g     same as above but left justified
  <P>
  %h          format as nn:nn:nn.n
  %15h        right justify nn:nn:nn.n in field of 15 characters
  %-15h       left justify nn:nn:nn.n in a field of 15 characters
  %12.2h      right justify nn:nn:nn.nn
  %-12.2h     left justify nn:nn:nn.nn
     
  %H          / by 15 and format as nn:nn:nn.n
  %15H        / by 15 and right justify nn:nn:nn.n in field of 15 characters
  %-15H       / by 15 and left justify nn:nn:nn.n in field of 15 characters
  %12.2H      / by 15 and right justify nn:nn:nn.nn
  %-12.2H     / by 15 and left justify nn:nn:nn.nn
  <P>
  \n          insert a newline
  </PRE>
  <P>
  </UL>
  <! EndSection:   'FORMATS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  1. Compute the transformation from the reference system to the output
  system and then evaluate the transformation for both the input list and
  the list of unknowns.
  <P>
     cl&gt; type rtran
  <P>
  	1.0000  1.0000 184.1445 -153.0376
  	512.0000 1.0000 684.0376 184.1445
  	512.0000 512.0000 346.8555 684.0376
  	1.0000 512.0000 -153.0380 346.8555
  <P>
      cl&gt; geomap rtran rtran.db 1.0 512.0 1.0 512.0 intera-
  <P>
      cl&gt; type rtran.db
  <P>
  	# Tue 14:53:36 18-Apr-95
  	begin	rtran
  		output		rtran.db
  		xrefmean	256.5
  		yrefmean	256.5
  		xmean		265.4999
  		ymean		265.5
  		xshift		183.826
  		yshift		-154.6757
  		xmag		1.180001
  		ymag		1.179999
  		xrotation	326.
  		yrotation	326.
  		surface1	11
  				3.	3.
  				2.	2.
  				2.	2.
  				0.	0.
  				1.	1.
  				512.	512.
  				1.	1.
  				512.	512.
  				183.826	-154.6757
  				0.9782647	0.6598474
  				-0.6598479	0.9782643
  	    	surface2	0
  <P>
      cl&gt; geoxytran rtran STDOUT rtran.db rtran
  <P>
  	184.1444 -153.038 184.1445 -153.0376
  	684.0377 184.1444 684.0376 184.1445
  	346.8554 684.0375 346.8555 684.0376
  	-153.038 346.8555 -153.038 346.8555
  <P>
      cl&gt; geoxytran unknowns unknowns.tran rtran.db rtran
  <P>
  <P>
  2.  Evaluate the backward transformation to take coordinates from the
  output system to the reference system.  In this example we use the
  output of the first example to illustrate getting back the coordinates
  used in the original geomap input.
  <P>
      cl&gt; geoxytran rtran STDOUT rtran.db rtran dir=forward |\<BR>
      &gt;&gt;&gt; geoxytran STDIN STDOUT rtran.db rtran dir=backward
      0.999798 0.9997257 184.1445 -153.0376
          512. 0.9999674 684.0376 184.1445
  	512.     512. 346.8555 684.0376
      0.999918 512.0001 -153.0380 346.8555
  <P>
  <P>
  3. Evaluate the transform computed in example 1 for the same list of
  unknowns but modify the transformation slightly by setting xmag
  and ymag to 1.18 and 1.18 exactly.
  <P>
      cl&gt; geoxytran unknowns unknowns.tran rtran.db rtran xmag=1.18 \<BR>
  	ymag=1.18
  <P>
  <P>
  4. Evaluate the same transformation for the same unknowns as before
  using the linear transformation parameters not the transform computed
  by geomap. Note that the angle is the negative of the one defined
  in the database file.
  <P>
      cl&gt; geoxytran unknowns unknowns.tran "" xmag=1.18 ymag=1.18 \<BR>
          xrot=34 yrot=34 xshift=183.826 yshift=-154.6757
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  geomap, lists.lintran, geotran, gregister
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'Forward vs. Backward Transformations' 'FORMATS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>