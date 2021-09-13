ccxymatch — Match celestial and pixel coordinate lists
======================================================

**Package: imcoords**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ccxymatch (Oct96)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imcoords</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ccxymatch (Oct96)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ccxymatch</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ccxymatch -- Match celestial and pixel coordinate lists using various methods
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  ccxymatch input reference output tolerance [ptolerance]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input pixel coordinate files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reference">reference</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>The list of input celestial coordinate files. The number of celestial coordinate
  files must be one or equal to the number of pixel coordinate files.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output matched coordinate files containing: 1) the celestial coordinates
  of the matched objects in columns 1 and 2, 2) the pixel coordinates of the
  matched objects in columns 3 and 4, and 3) the line numbers of the matched
  objects in the celestial coordinate and pixel lists in columns 5 and 6.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tolerance">tolerance</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='tolerance' Line='tolerance'>
  <DD>The matching tolerance in arcseconds. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ptolerance">ptolerance</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ptolerance' Line='ptolerance'>
  <DD>The matching tolerance in pixels. The ptolerance parameter is required 
  by the "<TT>triangles</TT>" matching algorithm but not by the "<TT>tolerance</TT>" matching
  algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_refpoints">refpoints = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refpoints' Line='refpoints = ""'>
  <DD>A file of tie points used to compute the linear transformation
  from the pixel coordinate system to the celestial coordinate system. Refpoints
  is a text file containing the celestial coordinates of 1-3 tie points
  in the first line, followed by the pixel coordinates of the same 1-3 tie points
  in succeeding lines. The celestial coordinates are assumed to be
  in the units specified by <I>lngunits</I> and <I>latunits</I>.
  If refpoints is undefined then the parameters <I>xin</I>, <I>yin</I>,
  <I>xmag</I>, <I>ymag</I>, <I>xrotation</I>, <I>yrotation</I>, <I>projection</I>,
  <I>lngref</I>, and <I>latref</I> are used to compute the linear transformation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xin">xin = INDEF, yin = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xin' Line='xin = INDEF, yin = INDEF'>
  <DD>The x and y origin of the pixel coordinate system. Xin and yin default to 
  0.0 and 0.0 respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmag">xmag = INDEF, ymag = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag = INDEF, ymag = INDEF'>
  <DD>The x and y scale factors in arcseconds per pixel. Xmag and
  ymag default to 1.0 and 1.0 respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xrotation">xrotation = INDEF, yrotation = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xrotation' Line='xrotation = INDEF, yrotation = INDEF'>
  <DD>The x and y rotation angles measured in degrees counter-clockwise. Xrotation
  and yrotation default to 0.0 and 0.0 degrees respectively. To set east to the
  up, down, left, and right directions, set xrotation to 90, 270, 180, and 0
  respectively. To set north to the up, down, left, and right directions, set
  yrotation to  0, 180, 90, and 270 degrees respectively. Any global rotation
  must be added to both the xrotation and yrotation values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_projection">projection = "<TT>tan</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='projection' Line='projection = "tan"'>
  <DD>The sky projection geometry. The most commonly used projections in
  astronomy are "<TT>tan</TT>", "<TT>arc</TT>", "<TT>sin</TT>", and "<TT>lin</TT>". Other supported projections
  are "<TT>ait</TT>", "<TT>car</TT>", "<TT>csc</TT>", "<TT>gls</TT>", "<TT>mer</TT>", "<TT>mol</TT>", "<TT>par</TT>", "<TT>pco</TT>", "<TT>qsc</TT>", "<TT>stg</TT>",
  "<TT>tsc</TT>", and "<TT>zea</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngref">lngref = INDEF, latref = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngref' Line='lngref = INDEF, latref = INDEF'>
  <DD>The origin of the celestial coordinate system. Lngref and latref define the
  reference point of the sky projection <I>projection</I>, and default to the
  mean of the ra / longitude and dec / latitude coordinates respectively. Lngref
  and latref are assumed to be in units of <I>lngunits</I> and <I>latunits</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngcolumn">lngcolumn = 1, latcolumn = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngcolumn' Line='lngcolumn = 1, latcolumn = 2'>
  <DD>The columns in the celestial coordinate list containing the ra / longitude
  and dec / latitude coordinate values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xcolumn">xcolumn = 1, ycolumn = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcolumn' Line='xcolumn = 1, ycolumn = 2'>
  <DD>The columns in the pixel coordinate list containing the x and y coordinate
  values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngunits">lngunits = "<TT>hours</TT>", latunits = "<TT>degrees</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngunits' Line='lngunits = "hours", latunits = "degrees"'>
  <DD>The units of the celestial coordinates. The options are "<TT>hours</TT>", "<TT>degrees</TT>",
  and "<TT>radians</TT>" for lngunits, and "<TT>degrees</TT>" and "<TT>radians</TT>" for latunits.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_separation">separation = 3.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='separation' Line='separation = 3.0'>
  <DD>The minimum separation in arcseconds for objects in the celestial coordinate
  lists. Objects closer together than separation arcseconds
  are removed from the celestial coordinate lists prior to matching.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pseparation">pseparation = 9.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pseparation' Line='pseparation = 9.0'>
  <DD>The minimum separation in pixels  for objects in the pixel coordinate
  lists. Objects closer together than pseparation pixels
  are removed from the pixel coordinate lists prior to matching.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_matching">matching = "<TT>triangles</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='matching' Line='matching = "triangles"'>
  <DD>The matching algorithm. The choices are:
  <DL>
  <DT><B><A NAME="l_tolerance">tolerance</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='tolerance' Line='tolerance'>
  <DD>A linear transformation is applied to the pixel coordinates,
  the appropriate projection is applied to the celestial coordinates,
  the transformed pixel and celestial coordinates are sorted, 
  points which are too close together are removed, and the pixel coordinates
  which most closely match the celestial coordinates to within the
  user specified tolerance are determined.  The tolerance algorithm requires
  an initial estimate for the linear transformation.  This estimate can be
  derived by supplying the coordinates of tie points via the
  <I>refpoints</I> file, or by setting the linear transformation parameters
  <I>xin</I>, <I>yin</I>, <I>xmag</I>, <I>ymag</I>, <I>xrotation</I>,
  <I>yrotation</I>, <I>projection</I>, <I>lngref</I>, and <I>latref</I>. Assuming that
  a good initial estimate for the required linear transformation is supplied,
  the tolerance algorithm functions well in the presence of shifts, axis
  flips, x and y scale changes, rotations, and axis skew between the two
  coordinate systems. The algorithm is sensitive to higher order distortion terms
  in the coordinate transformation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_triangles">triangles</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='triangles' Line='triangles'>
  <DD>A linear transformation is applied to the pixel coordinates,
  the appropriate projection is applied to the celestial coordinates,
  the transformed pixel and celestial coordinates are sorted, points
  which are too close together are removed, and the pixel coordinates
  are matched to the celestial coordinates using a triangle pattern
  matching algorithm and user specified tolerance parameters.
  The triangles pattern matching algorithm does not require prior knowledge
  of the linear transformation, although it will use a transformation if one
  is supplied.  The algorithm functions well in the presence of
  shifts, axis flips, magnification, and rotation between the two coordinate
  systems, as long as both lists have a reasonable number of objects
  in common and the errors in the computed coordinates are small.
  However as the algorithm depends on comparisons of similar triangles, it
  is sensitive to differences in the x and y coordinate scales,
  skew between the x and y axes, and higher order distortion terms
  in the coordinate transformation.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nmatch">nmatch = 30</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nmatch' Line='nmatch = 30'>
  <DD>The maximum number of celestial and pixel coordinates used
  by the "<TT>triangles</TT>" pattern matching algorithm. If either list contains
  more coordinates than nmatch, the lists are subsampled. Nmatch should be
  kept small as the computation and memory requirements of the "<TT>triangles</TT>"
  algorithm depend on a high power of the lengths of the respective lists.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ratio">ratio = 10.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ratio' Line='ratio = 10.0'>
  <DD>The maximum ratio of the longest to shortest side of the 
  triangles generated by the "<TT>triangles</TT>" pattern matching algorithm.
  Triangles with computed longest to shortest side ratios &gt; ratio
  are rejected from the pattern matching algorithm. Ratio should never
  be set higher than 10.0 but may be set as low as 5.0.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nreject">nreject = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nreject' Line='nreject = 10'>
  <DD>The maximum number of rejection iterations for the "<TT>triangles</TT>" pattern
  matching algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lngformat">lngformat = "<TT></TT>", latformat = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngformat' Line='lngformat = "", latformat = ""'>
  <DD>The format of the output celestial coordinates. The default formats are
  "<TT>%13.3h</TT>", "<TT>%13.3h</TT>", and "<TT>%13.7g</TT>" for units of "<TT>hours</TT>", "<TT>degrees</TT>", and
  "<TT>radians</TT>" respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xformat">xformat = "<TT>%13.3f</TT>", yformat = "<TT>%13.3f</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xformat' Line='xformat = "%13.3f", yformat = "%13.3f"'>
  <DD>The format of the output pixel coordinates.
  By default the coordinates are output right justified in a field of
  13 characters with 3 places following the decimal point.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about the progress of the task ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  CCXYMATCH matches ra / dec or longitude / latitude coordinates in the
  celestial coordinate list <I>reference</I> to their corresponding x and y
  coordinates in the pixel coordinate list <I>input</I> using user specified
  tolerances in arcseconds <I>tolerance</I> and pixels <I>ptolerance</I>, and 
  writes the matched coordinates to the output file <I>output</I>. The output
  file is suitable for input to the plate solution computation task CCMAP.
  <P>
  CCXYMATCH matches the coordinate lists by: 1) projecting the celestial
  coordinates onto a plane using the sky projection geometry <I>projection</I>
  and the reference point <I>lngref</I> and <I>latref</I>,
  2) computing an initial guess for the linear transformation required to
  match the pixel coordinate system to the projected celestial coordinate system,
  3) applying the computed transformation to the pixel coordinates, 4) sorting
  the projected celestial and pixel coordinates lists, 5) removing points with a
  minimum separation specified by the parameters <I>separation</I> and
  <I>pseparation</I> from both lists, 6) matching the two lists using either
  the "<TT>triangles</TT>" or "<TT>tolerance</TT>" matching algorithms, and 7) writing the matched
  list to the output file.
  <P>
  An initial estimate for the linear transformation is computed in one of 
  two ways. If <I>refpoints</I> is defined, the celestial and pixel coordinates
  of up to three tie points are read from succeeding lines in the refpoints file,
  and used to compute the linear transformation.  The coordinates of the tie
  points can be typed in by hand if <I>refpoints</I> is "<TT>STDIN</TT>". The formats of
  two sample refpoints files are shown below.
  <P>
  <PRE>
  # First sample refpoints file (1 reference file and N input files)
  <P>
  ra1 dec1  [ra2 dec2 [ra3 dec3]] # tie points for reference coordinate file
   x1   y1  [ x2  y2  [ x3   y3]] # tie points for input coordinate file 1
   x1   y1  [ x2  y2  [ x3   y3]] # tie points for input coordinate file 2
   x1   y1  [ x2  y2  [ x3   y3]] # tie points for input coordinate file N
  <P>
  <P>
  # Second sample refpoints file (N reference files and N input files)
  <P>
  ra1 dec1  [ra2 dec2 [ra3 dec3]] # tie points for reference coordinate file 1
   x1   y1  [ x2   y2 [ x3   y3]] # tie points for input coordinate file 1
  ra1 dec1  [ra2 dec2 [ra3 dec3]] # tie points for reference coordinate file 2
   x1   y1  [ x2   y2 [ x3   y3]] # tie points for input coordinate file 2
   ..   ..  [ ..   .. [ ..   ..]]
  ra1 dec1  [ra2 dec2 [ra3 dec3]] # tie points for reference coordinate file N
   x1   y1  [ x2   y2 [ x3   y3]] # tie points for input coordinate file N
  <P>
  </PRE>
  <P>
  If the refpoints file is undefined the parameters <I>xin</I>, <I>xin</I>,
  <I>xmag</I>, <I>ymag</I>, <I>xrotation</I>, <I>xrotation</I> are used
  to compute a linear transformation from the pixel coordinates to the
  standard coordinates xi and eta as shown below. Orientation and skew
  are the orientation of the x and y axes and their deviation from
  perpendicularity respectively.
  <P>
  <P>
  <PRE>
  	 xi = a + b * x + c * y
  	eta = d + e * x + f * y
      
  	xrotation = orientation - skew / 2
  	yrotation = orientation + skew / 2
  	b = xmag * cos (xrotation)
  	c = -ymag * sin (yrotation)
  	e = xmag * sin (xrotation)
  	f = ymag * cos (yrotation)
  	a = 0.0 - b * xin - c * yin = xshift
  	d = 0.0 - e * xin - f * yin = yshift
  </PRE>
  <P>
  Both methods of computing the initial linear transformation compute the
  standard coordinates xi and eta by projecting the celestial coordinates
  onto a plane using the sky projection geometry <I>projection</I> and the
  reference point <I>lngref</I> and <I>latref</I>. The celestial coordinates
  are assumed to be in units of <I>lngunits</I> and <I>latunits</I> and the
  standard coordinates are in arcseconds. The linear transformation and its
  geometric interpretation are shown below.
  <P>
  The celestial and pixel coordinates are read from columns <I>lngcolumn</I> and
  <I>latcolumn</I> in the celestial coordinate list, and <I>xcolumn</I>, and
  <I>ycolumn</I> in the pixel coordinate list respectively. The pixel
  coordinates are transformed using the linear transformation described above,
  the celestial coordinate in units of <I>lngunits</I> and <I>latunits</I>
  are projected to standard coordinates in arcseconds, and stars closer together
  than <I>separation</I> arcseconds and <I>pseparation</I> pixels are removed
  from the celestial and pixel coordinate lists respectively.
  <P>
  The coordinate lists are matched using the matching algorithm specified by
  <I>matching</I>. If matching is "<TT>tolerance</TT>", CCXYMATCH searches the transformed
  sorted pixel coordinate list for the coordinates that are within the matching
  tolerance <I>tolerance</I> and closest to the current standard coordinates.
  The major advantage of the "<TT>tolerance</TT>" algorithm is that it can handle x and y
  scale differences and axis skew in the coordinate transformation. The major
  disadvantage of the "<TT>tolerance</TT>" algorithm is that the user must supply
  tie point information in all but the simplest case of small x and y
  shifts between the pixel and celestial coordinate systems.
  <P>
  If matching is "<TT>triangles</TT>", CCXYMATCH constructs a list of triangles
  using up to <I>nmatch</I> celestial coordinates and transformed pixel
  coordinates and performs a pattern matching operation on the resulting
  triangle lists. If the number of coordinates in both lists is less than
  <I>nmatch</I> the entire list is matched using the "<TT>triangles</TT>" algorithm
  directly, otherwise the "<TT>triangles</TT>" algorithm is used to estimate a new
  linear transformation, the input coordinate list is transformed using
  the new transformation, and the entire list is matched using the "<TT>tolerance</TT>"
  algorithm. The major advantage of the "<TT>triangles</TT>" algorithm is that it
  requires no tie point information from the user. The major disadvantages of the
  algorithm are that, it is sensitive to x and y scale differences and axis
  skew between the celestial and pixel coordinate systems, and can be
  computationally expensive.
  <P>
  The matched celestial and pixel coordinates are written to columns 1, 2, 3,
  and 4 of the output file, in the formats specified by the <I>lngformat</I>,
  <I>latformat</I>, <I>xformat</I> and <I>yformat</I> parameters.  The original
  line numbers in the celestial and pixels coordinate files are written to
  columns 5 and 6.
  <P>
  If <I>verbose</I> is yes, detailed messages about actions taken by the
  task are written to the terminal as the task executes.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_algorithms">ALGORITHMS</A></H2>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  The "<TT>triangles</TT>" algorithm uses a sophisticated pattern matching
  technique which requires no tie point information from the user.
  It is expensive computationally and is therefore restricted to a maximum
  of <I>nmatch</I> objects from the celestial and pixel coordinate lists.
  <P>
  The "<TT>triangles</TT>" algorithm first generates a list
  of all the possible triangles that can be formed from the points in each list.
  For a list of nmatch points this number is the combinatorial factor
  nmatch! / [(nmatch-3)! * 3!] or  nmatch * (nmatch-1) * (nmatch-2) / 6.
  The length of the perimeter, ratio of longest to shortest side, cosine
  of the angle between the longest and shortest side, the tolerances in
  the latter two quantities and the direction of the arrangement of the vertices
  of each triangle are computed and stored in a table.
  Triangles with vertices closer together than <I>tolerance</I> and
  <I>ptolerance</I>, or
  with a ratio of the longest to shortest side greater than <I>ratio</I>
  are discarded. The remaining triangles are sorted in order of increasing
  ratio.  A sort merge algorithm is used to match the triangles using the
  ratio and cosine information, the tolerances in these quantities, and
  the maximum tolerances for both lists. The ratios of the
  perimeters of the matched triangles are compared to the most common ratio
  for the entire list, and triangles which deviate too widely from this number
  are discarded. The number of triangles remaining are divided into
  the number which match in the clockwise sense and the number which match
  int the counter-clockwise sense. Those in the minority category
  are eliminated.
  The rejection step can be repeated up to <I>nreject</I> times or until
  no more rejections occur, whichever comes first.
  The last step in the algorithm is a voting procedure in which each remaining
  matched triangle casts three votes, one for each matched pair of vertices.
  Points which have fewer than half the maximum number of
  votes are discarded. The final set of matches are written to the output file.
  <P>
  The "<TT>triangles</TT>" algorithm functions well when the celestial and
  pixel coordinate lists have a sufficient number of objects (50%, 
  in some cases as low as 25%) of their objects in common, any distortions
  including x and y scale differences and skew between the two systems are small,
  and the random errors in the coordinates are small. Increasing the value of
  the <I>tolerance</I> parameter will increase the ability to deal with
  distortions but will also produce more false matches which after some point
  will swamp the true matches.
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
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
   
  <P>
  <P>
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
  <H2><A NAME="s_references">REFERENCES</A></H2>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  A detailed description of the "<TT>triangles</TT>" pattern matching algorithm used here
  can be found in the article "<TT>A Pattern-Matching Algorithm for Two-
  Dimensional Coordinate Lists</TT>" by E.J. Groth, A.J. 91, 1244 (1986).
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute the plate solution for a 1528 by 2288 B band image of M51 by
  matching a list of reference stars extracted from the Guide Star Catalog
  with the regions task against a list of bright stars detected with the daofind
  task. The approximate image center is RA = 13:29:52.8 and DEC = +47:11:41
  (J2000) and the image scale is 0.43 arcseconds / pixel.
  <P>
  <PRE>
  cl&gt; regions 13:29:52.8 47:11:41 0.27 m51b.gsc.tab
  <P>
  cl&gt; tprint  m51b.gsc.tab &gt; m51b.gsc
  <P>
  cl&gt; type m51b.gsc
  <P>
  #  Table m51b.gsc.tab  Tue 10:39:55 22-Oct-96
  <P>
  # row      RA_HRS      RA_DEG     DEC_DEG        MAG
  #           hours     degrees     degrees magnitudes
  <P>
      1 13:29:13.33 202:18:19.9  47:14:16.3       12.3
      2 13:29:05.51 202:16:22.6  47:10:44.7       14.8
      3 13:29:48.60 202:27:09.0  47:07:42.5       15.0
      4 13:29:47.30 202:26:49.4  47:13:37.5       10.9
      5 13:29:31.65 202:22:54.7  47:18:54.7       15.0
      6 13:29:06.16 202:16:32.4  47:04:53.1       14.9
      7 13:29:37.40 202:24:21.1  47:09:09.2       15.1
      8 13:29:38.70 202:24:40.5  47:13:36.2       15.0
      9 13:29:55.42 202:28:51.3  47:10:05.2       15.4
     10 13:29:06.91 202:16:43.7  47:04:07.9       12.4
     11 13:29:29.73 202:22:25.9  47:12:04.1       15.1
     12 13:30:07.96 202:31:59.4  47:05:18.3       14.7
     13 13:30:01.82 202:30:27.2  47:12:58.8       11.8
     14 13:30:36.75 202:39:11.2  47:04:05.9       14.9
     15 13:30:34.04 202:38:30.6  47:16:44.8       13.2
     16 13:30:14.95 202:33:44.3  47:10:27.6       13.4
  <P>
  cl&gt; daofind m51b "default" fwhmpsf=4.0 sigma=5.0 threshold=20.0
  <P>
  cl&gt; type m51b.coo.1
  <P>
     ...
  #N XCENTER   YCENTER   MAG      SHARPNESS   SROUND      GROUND      ID 
     ...
     401.034   147.262   -2.315   0.473       -0.075      -0.170      1     
     261.137   453.696   -1.180   0.481       -0.373      -0.135      2     
     860.002   480.061   -1.397   0.373       -0.218      -0.178      3     
     69.342    675.895   -0.955   0.368       -0.294      -0.133      4     
     1127.791  680.033   -1.166   0.449       -0.515      -0.326      5     
     972.435   691.544   -1.722   0.449       -0.327      -0.060      6     
     1348.891  715.084   -1.069   0.389       -0.242      -0.145      7     
     946.114   797.067   -0.543   0.406       -0.198      -0.069      8     
     698.455   811.407   -1.620   0.437       -0.038      -0.028      9     
     964.566   853.201   -0.317   0.382       0.031       -0.086      10    
     236.088   864.817   -3.515   0.429       -0.164      -0.035      11    
     919.703   909.835   -3.775   0.447       0.051       0.007       12    
     406.592   985.807   -0.715   0.424       -0.307      -0.068      13    
     920.790   986.083   -0.600   0.364       -0.047      0.021       14    
     761.403   1037.795  -1.944   0.383       -0.023      0.120       15    
     692.012   1050.603  -0.508   0.339       -0.365      -0.164      16    
     1023.330  1060.144  -1.897   0.381       -0.246      -0.288      17    
     681.864   1066.937  -0.059   0.467       -0.175      0.135       18    
     1307.802  1085.564  -1.173   0.435       0.032       -0.207      19    
     716.494   1094.800  -0.389   0.421       -0.412      -0.032      20    
     715.935   1106.616  -3.747   0.649       0.271       0.245       21    
     1093.813  1300.189  -1.557   0.377       -0.309      -0.078      22    
     596.406   1353.798  -0.461   0.383       0.029       -0.103      23    
     1212.117  1362.636  -0.362   0.369       -0.180      0.043       24    
     251.355   1488.048  -0.909   0.357       -0.390      0.077       25    
     600.659   1630.261  -1.392   0.423       0.013       -0.312      26    
     329.448   2179.233  -0.824   0.442       -0.463      0.325       27    
  <P>
  cl&gt; ccxymatch m51b.coo.1 m51b.gsc m51b.mat.1 1.0 3.0 lngcolumn=2 latcolumn=4
  <P>
  cl&gt; type m51b.mat.1
  <P>
  # Input: m51b.coo.1  Reference: m51b.gsc  Number of tie points: 0
  # Initial linear transformation
  #     xref[tie] =         0. +         1. * x[tie] +         0. * y[tie]
  #     yref[tie] =         0. +         0. * x[tie] +         1. * y[tie]
  # dx: 0.00 dy: 0.00 xmag: 1.000 ymag: 1.000 xrot: 0.0 yrot: 0.0
  #
  # Column definitions
  #    Column 1: Reference Ra / Longitude coordinate
  #    Column 2: Reference Dec / Latitude coordinate
  #    Column 3: Input X coordinate
  #    Column 4: Input Y coordinate
  #    Column 5: Reference line number
  #    Column 6: Input line number
  <P>
   13:29:48.600   47:07:42.50        860.002       480.061      8    44
   13:29:38.700   47:13:36.20       1093.813      1300.189     13    63
   13:29:55.420   47:10:05.20        698.455       811.407     14    50
   13:29:29.730   47:12:04.10       1307.802      1085.564     16    60
   13:30:07.960   47:05:18.30        401.034       147.262     17    42
   13:30:14.950   47:10:27.60        236.088       864.817     21    52
  <P>
  cl&gt; ccmap m51b.mat.1 ccmap.db results=STDOUT xcolumn=3 ycolumn=4 lngcolumn=1 \<BR>
  latcolumn=2 refpoint=user lngref=13:29:52.8 latref=47:11:41  interactive=no
  <P>
  Coords File: m51b.mat.1  Image: 
      Database: ccmap.db  Record: m51b.mat.1
  Refsystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.000 MJD: 51544.50000
  Insystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.000 MJD: 51544.50000
  Coordinate mapping status
      XI fit ok.  ETA fit ok.
      Ra/Dec or Long/Lat fit rms: 0.206  0.103   (arcsec  arcsec)
  Coordinate mapping parameters
      Sky projection geometry: tan
      Reference point: 13:29:52.800  47:11:41.00  (hours  degrees)
      Reference point: 760.656  1033.450  (pixels  pixels)
      X and Y scale: 0.430  0.431  (arcsec/pixel  arcsec/pixel)
      X and Y axis rotation: 180.158  359.991  (degrees  degrees)
  <P>
                          Input Coordinate Listing
     X      Y        Ra         Dec        Ra(fit)    Dec(fit)    Dra    Ddec
  <P>
   860.0  480.1  13:29:48.60 47:07:42.5  13:29:48.62 47:07:42.5 -0.153  0.017
  1093.8 1300.2  13:29:38.70 47:13:36.2  13:29:38.73 47:13:36.4 -0.258 -0.164
   698.5  811.4  13:29:55.42 47:10:05.2  13:29:55.43 47:10:05.2 -0.062  0.024
  1307.8 1085.6  13:29:29.73 47:12:04.1  13:29:29.70 47:12:04.0  0.318  0.123
   401.0  147.3  13:30:07.96 47:05:18.3  13:30:07.96 47:05:18.4  0.028 -0.073
   236.1  864.8  13:30:14.95 47:10:27.6  13:30:14.94 47:10:27.5  0.127  0.073
  </PRE>
  <P>
  <P>
  <P>
  2. Repeat example 1 but replace the daofind pixel list with one generated
  using the center task and a finder chart created with the skymap task.
  <P>
  <PRE>
  cl&gt; regions 13:29:52.8 47:11:41 0.27 m51b.gsc.tab
  <P>
  cl&gt; gasp.skymap m51b.gsc.tab 13:29:52.8 47:11:41 INDEF 0.27            \<BR>
  objstyle=square racol=RA_HRS deccol=DEC_DEG magcol=MAG interactive-    \<BR>
  dev=stdplot
  <P>
  cl&gt; tprint  m51b.gsc.tab &gt; m51b.gsc
  <P>
  cl&gt; display m51b 1 fi+
  cl&gt; center m51b cbox=7.0 ...
  cl&gt; pdump m51b.ctr.1 xcenter,ycenter yes &gt; m51b.pix 
  <P>
  cl&gt; type m51b.pix
  <P>
  401.022  147.183
  236.044  864.882
  698.368  811.329
  860.003  480.051
  1127.754  680.020
  1307.819  1085.615
  1093.464  1289.595
  1212.001  1362.594
  1348.963  715.085
  <P>
  cl&gt; ccxymatch m51b.pix m51b.gsc m51b.mat.2 1.0 3.0 lngcolumn=2 latcolumn=4
  <P>
  cl&gt; type m51b.mat.2
  <P>
  # Input: m51b.pix  Reference: m51b.gsc  Number of tie points: 0
  # Initial linear transformation
  #       xi[tie] =         0. +         1. * x[tie] +         0. * y[tie]
  #      eta[tie] =         0. +         0. * x[tie] +         1. * y[tie]
  # dx: 0.00 dy: 0.00 xmag: 1.000 ymag: 1.000 xrot: 0.0 yrot: 0.0
  #
  # Column definitions
  #    Column 1: Reference Ra / Longitude coordinate
  #    Column 2: Reference Dec / Latitude coordinate
  #    Column 3: Input X coordinate
  #    Column 4: Input Y coordinate
  #    Column 5: Reference line number
  #    Column 6: Input line number
  <P>
   13:29:48.600   47:07:42.50        860.003       480.051      8     4
   13:29:37.400   47:09:09.20       1127.754       680.020     12     5
   13:29:55.420   47:10:05.20        698.368       811.329     14     3
   13:29:29.730   47:12:04.10       1307.819      1085.615     16     6
   13:30:07.960   47:05:18.30        401.022       147.183     17     1
   13:30:14.950   47:10:27.60        236.044       864.882     21     2
  <P>
  cl&gt; ccmap m51b.mat.2 ccmap.db results=STDOUT xcolumn=3 ycolumn=4 lngcolumn=1 \<BR>
  latcolumn=2 refpoint=user lngref=13:29:52.8 latref=47:11:41 interactive=no
  <P>
  Coords File: m51b.mat.2  Image: 
      Database: junk.db  Record: m51b.mat.2
  Refsystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.000 MJD: 51544.50000
  Insystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.000 MJD: 51544.50000
  Coordinate mapping status
      XI fit ok.  ETA fit ok.
      Ra/Dec or Long/Lat fit rms: 0.312  0.0664   (arcsec  arcsec)
  Coordinate mapping parameters
      Sky projection geometry: tan
      Reference point: 13:29:52.800  47:11:41.00  (hours  degrees)
      Reference point: 761.093  1033.230  (pixels  pixels)
      X and Y scale: 0.430  0.431  (arcsec/pixel  arcsec/pixel)
      X and Y axis rotation: 180.175  359.998  (degrees  degrees)
  <P>
                          Input Coordinate Listing
     X      Y        Ra         Dec        Ra(fit)    Dec(fit)    Dra    Ddec
  </PRE>
  <P>
  <P>
  3. Repeat example 1 but use the "<TT>tolerance</TT>" matching algorithm and apriori
  knowledge of the celestial and pixel coordinates of the nucleus of M51,
  the x and y image scales, and the orientation of the detector on the telescope
  to match the two lists.
  <P>
  <PRE>
  cl&gt; ccxymatch m51b.coo.1 m51b.gsc m51b.mat.3 2.0 lngcolumn=2 latcolumn=4 \<BR>
  matching=tolerance xin=761.40 yin=1037.80 xmag=-0.43 ymag=0.43 xrot=0.0  \<BR>
  yrot=0.0 lngref=13:29:52.80 latref=47:11:42.9
  <P>
  cl&gt; type m51b.mat.3
  <P>
  # Input: m51b.coo.1  Reference: m51b.gsc  Number of tie points: 0
  # Initial linear transformation
  #     xref[tie] =    327.402 +      -0.43 * x[tie] +         0. * y[tie]
  #     yref[tie] =   -446.254 +         0. * x[tie] +       0.43 * y[tie]
  # dx: 327.40 dy: -446.25 xmag: 0.430 ymag: 0.430 xrot: 180.0 yrot: 0.0
  #
  # Column definitions
  #    Column 1: Reference Ra / Longitude coordinate
  #    Column 2: Reference Dec / Latitude coordinate
  #    Column 3: Input X coordinate
  #    Column 4: Input Y coordinate
  #    Column 5: Reference line number
  #    Column 6: Input line number
  <P>
   13:30:07.960   47:05:18.30        401.034       147.262     17    42
   13:29:48.600   47:07:42.50        860.002       480.061      8    44
   13:29:37.400   47:09:09.20       1127.791       680.033     12    46
   13:29:55.420   47:10:05.20        698.455       811.407     14    50
   13:30:14.950   47:10:27.60        236.088       864.817     21    52
   13:29:29.730   47:12:04.10       1307.802      1085.564     16    60
   13:29:38.700   47:13:36.20       1093.813      1300.189     13    63
  <P>
  <P>
  cl&gt; ccmap m51b.mat.3 ccmap.db results=STDOUT xcolumn=3 ycolumn=4 lngcolumn=1 \<BR>
  latcolumn=2 refpoint=user lngref=13:29:52.8 latref=47:11:41 interactive=no
  <P>
  Coords File: m51b.mat.3  Image: 
      Database: ccmap.db  Record: m51.mat.3
  Refsystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.000 MJD: 51544.50000
  Insystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.000 MJD: 51544.50000
  Coordinate mapping status
      XI fit ok.  ETA fit ok.
      Ra/Dec or Long/Lat fit rms: 0.342  0.121   (arcsec  arcsec)
  Coordinate mapping parameters
      Sky projection geometry: tan
      Reference point: 13:29:52.800  47:11:41.00  (hours  degrees)
      Reference point: 760.687  1033.441  (pixels  pixels)
      X and Y scale: 0.430  0.431  (arcsec/pixel  arcsec/pixel)
      X and Y axis rotation: 180.174  359.949  (degrees  degrees)
  <P>
                          Input Coordinate Listing
     X      Y        Ra         Dec        Ra(fit)    Dec(fit)    Dra    Ddec
  <P>
   401.0  147.3  13:30:07.96 47:05:18.3  13:30:07.97 47:05:18.4 -0.109 -0.109
   860.0  480.1  13:29:48.60 47:07:42.5  13:29:48.64 47:07:42.5 -0.385 -0.045
  1127.8  680.0  13:29:37.40 47:09:09.2  13:29:37.34 47:09:09.0  0.572  0.152
   698.5  811.4  13:29:55.42 47:10:05.2  13:29:55.43 47:10:05.2 -0.118  0.009
   236.1  864.8  13:30:14.95 47:10:27.6  13:30:14.92 47:10:27.5  0.290  0.116
  1307.8 1085.6  13:29:29.73 47:12:04.1  13:29:29.72 47:12:04.0  0.082  0.060
  1093.8 1300.2  13:29:38.70 47:13:36.2  13:29:38.73 47:13:36.4 -0.332 -0.184
  </PRE>
  <P>
  <P>
  <P>
  4. Repeat example 3 but input the appropriate linear transformation via a list
  of tie points, rather than setting the transformation parameters directly.
  <P>
  <PRE>
  cl&gt; type refpts
  13:29:55.42 47:10:05.2  13:29:38.70 47:13:36.2  13:30:14.95 47:10:27.6
       698.5       811.4      1093.8      1300.2       236.1       864.8
  <P>
  cl&gt; ccxymatch m51b.coo.1 m51b.gsc m51b.mat.4 2.0 refpoints=refpts          \<BR>
  lngcolumn=2 latcolumn=4 matching=tolerance lngref=13:29:52.80              \<BR>
  latref=47:11:42.9
  <P>
  cl&gt; type m51b.mat.4
  <P>
  # Input: m51b.coo.1  Reference: m51b.gsc  Number of tie points: 3
  #     tie point:   1  ref:    26.718   -97.698  input:   698.500   811.400
  #     tie point:   2  ref:  -143.629   113.354  input:  1093.800  1300.200
  #     tie point:   3  ref:   225.854   -75.167  input:   236.100   864.800
  #
  # Initial linear transformation
  #       xi[tie] =   327.7137 + -0.4306799 * x[tie] + -2.0406E-4 * y[tie]
  #      eta[tie] =  -448.0854 + 0.00103896 * x[tie] +   0.430936 * y[tie]
  # dx: 327.71 dy: -448.09 xmag: 0.431 ymag: 0.431 xrot: 179.9 yrot: 0.0
  #
  # Column definitions
  #    Column 1: Reference Ra / Longitude coordinate
  #    Column 2: Reference Dec / Latitude coordinate
  #    Column 3: Input X coordinate
  #    Column 4: Input Y coordinate
  #    Column 5: Reference line number
  #    Column 6: Input line number
  <P>
  <P>
   13:30:07.960   47:05:18.30        401.034       147.262     17    42
   13:29:48.600   47:07:42.50        860.002       480.061      8    44
   13:29:37.400   47:09:09.20       1127.791       680.033     12    46
   13:29:55.420   47:10:05.20        698.455       811.407     14    50
   13:30:14.950   47:10:27.60        236.088       864.817     21    52
   13:29:29.730   47:12:04.10       1307.802      1085.564     16    60
   13:29:38.700   47:13:36.20       1093.813      1300.189     13    63
  <P>
  <P>
  cl&gt; ccmap m51b.mat.4 ccmap.db results=STDOUT xcolumn=3 ycolumn=4 lngcolumn=1 \<BR>
  latcolumn=2 refpoint=user lngref=13:29:52.8 latref=47:11:41 interactive=no
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  stsdas.gasp.regions,stsdas.gasp.skymap,tables.ttools.tprint,daophot.daofind,ccmap
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'ALGORITHMS' 'FORMATS' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>