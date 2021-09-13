.. _cctran:

cctran — Transform coordinate lists using the ccmap plate solution
==================================================================

**Package: imcoords**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  cctran -- transform from pixel to celestial coordinates and vice versa
  using the computed plate solution
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  cctran input output database solutions
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The coordinate files to be transformed.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output coordinate files. The number of output files must
  be one or equal to the number of input files.
  </DD>
  </DL>
  <DL>
  <DT><B>database</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The text database file written by the ccmap task containing the
  desired plate solution. If database is undefined cctran computes
  a linear plate solution using the current values of the xref, yref, xmag
  ymag, xrotation, yrotation, lngref, latref, and projection parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>solutions</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='solutions' Line='solutions'>
  <DD>The database record containing the desired plate solution. 
  The number of records must be one or equal to the number of input coordinate
  files. Solutions is either a user name supplied to ccmap, the name of the
  ccmap task
  input image for which the plate solution is valid, or the name of the
  coordinate file that the ccmap task used to compute the plate solution.
  The quantities stored in
  solutions always supersede the values of xref, yref, xmag, ymag,
  xrotation, yrotation, lngref, latref, and projection.
  </DD>
  </DL>
  <DL>
  <DT><B>geometry = "<TT>geometric</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='geometry' Line='geometry = "geometric"'>
  <DD>The type of geometric transformation. The geometry parameter is
  only requested if database is defined. The options are:
  <DL>
  <DT><B>linear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Transform the coordinates using only the linear part of the plate solution.
  </DD>
  </DL>
  <DL>
  <DT><B>geometric</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='geometric' Line='geometric'>
  <DD>Transform the coordinates using the full plate solution.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>forward = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='forward' Line='forward = yes'>
  <DD>Transform from pixel to celestial coordinates ? If forward is "<TT>no</TT>" then
  the plate solution is inverted and celestial coordinates are transformed
  to pixel coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>xref = INDEF, yref = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xref' Line='xref = INDEF, yref = INDEF'>
  <DD>The x and y pixel coordinates of the reference point. If database is undefined
  then xref and yref default to 0.0 and 0.0, otherwise these parameters are
  ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>xmag = INDEF, ymag = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag = INDEF, ymag = INDEF'>
  <DD>The x and y scale factors in arcseconds per pixel. If database is undefined
  xmag and ymag default to 1.0 and 1.0 arcseconds per pixel, otherwise these
  parameters are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>xrotation = INDEF, yrotation = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xrotation' Line='xrotation = INDEF, yrotation = INDEF'>
  <DD>The x and y rotation angles in degrees measured counter-clockwise with
  respect to the x and y axes. Xrotation and yrotation are interpreted as the
  rotation of the coordinates with respect to the x and y axes and default to
  0.0 and 0.0 degrees. For example xrotation and yrotation values of 30.0 and
  30.0 degrees will rotate a point 30 degrees counter-clockwise with respect to
  the x and y axes. To flip the x axis coordinates in this case either set the
  angles to 210.0 and 30.0 degrees or leave the angles at 30.0 and 30.0 and set
  the xmag parameter to a negative value. To set east to the up, down, left, and
  right directions, set xrotation to 90, 270, 180, and 0 respectively. To set
  north to the up, down, left, and right directions, set yrotation to  0, 180,
  90, and 270 degrees respectively. Any global rotation must be added to both the
  xrotation and yrotation values.
  </DD>
  </DL>
  <DL>
  <DT><B>lngref = INDEF, latref = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngref' Line='lngref = INDEF, latref = INDEF'>
  <DD>The celestial coordinates of the reference point, e.g. the ra and dec
  of the reference point for equatorial systems, galactic longitude and
  latitude for galactic systems. If database is undefined
  lngref and latred default to 0.0 and 0.0, otherwise these parameters are
  ignored.
  </DD>
  </DL>
  <DL>
  <DT><B>lngunits = "<TT></TT>", latunits = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngunits' Line='lngunits = "", latunits = ""'>
  <DD>The units of the input or output ra / longitude and dec / latitude coordinates.
  The options are "<TT>hours</TT>", "<TT>degrees</TT>", "<TT>radians</TT>" for ra / longitude coordinates,
  and "<TT>degrees</TT>" and "<TT>radians</TT>" for dec / latitude systems. If lngunits and
  latunits are undefined they default to the values in the database records.
  If database is undefined then lngunits and latunits default to "<TT>hours</TT>" and
  "<TT>degrees</TT>" respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>projection = "<TT>tan</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='projection' Line='projection = "tan"'>
  <DD>The sky projection geometry. The most commonly used projections in
  astronomy are "<TT>tan</TT>", "<TT>arc</TT>", "<TT>sin</TT>", and "<TT>lin</TT>". Other supported projections
  are "<TT>ait</TT>", "<TT>car</TT>", "<TT>csc</TT>", "<TT>gls</TT>", "<TT>mer</TT>", "<TT>mol</TT>", "<TT>par</TT>", "<TT>pco</TT>", "<TT>qsc</TT>", "<TT>stg</TT>",
  "<TT>tsc</TT>", and "<TT>zea</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>xcolumn = 1, ycolumn = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcolumn' Line='xcolumn = 1, ycolumn = 2'>
  <DD>The columns in the input coordinate file containing the x and y coordinates
  if the <I>forward</I> parameter is "<TT>yes</TT>", the celestial ra / longitude and
  dec / latitude if the forward parameter is "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>lngformat = "<TT></TT>", latformat = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lngformat' Line='lngformat = "", latformat = ""'>
  <DD>The format of the output coordinates. The defaults are "<TT>%10.3f</TT>" for 
  output coordinates in pixels, "<TT>%12.2h</TT>" for coordinates in hours,
  "<TT>%11.1h</TT>" for coordinates in degrees,
  and "<TT>%13.7g</TT>" for coordinates in radians.
  </DD>
  </DL>
  <DL>
  <DT><B>min_sigdigits = 7</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='min_sigdigits' Line='min_sigdigits = 7'>
  <DD>The minimum precision of the output coordinates.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  CCTRAN applies the plate solution to a list of pixel or celestial
  coordinates in the text file <I>input</I> and writes the transformed
  coordinates to the text file <I>output</I>. The input coordinates
  are read from and the output coordinates written to, the columns
  <I>xcolumn</I> and <I>ycolumn</I> in the input and output
  files. The format of the output coordinates can be specified using the
  <I>lngformat</I> and <I>latformat</I> parameters. If the output formats
  are unspecified the coordinates are written  out with reasonable
  default precisions, e.g. "<TT>%10.3f</TT>" for pixel coordinates, "<TT>%12.2h</TT>" and "<TT>11.1h</TT>"
  for coordinates in hours or degrees,
  and "<TT>%13.7g</TT>" for coordinates in radians. All the remaining fields in the
  input file are copied to the output file without modification. Blank lines
  and comment lines are also passed to the output file unaltered.
  <P>
  The plate solution is either read from record <I>solutions</I>
  in the database file <I>database</I> written by CCMAP, or specified
  by the user via the <I>xref</I>, <I>yref</I>, <I>xmag</I>, <I>ymag</I>,
  <I>xrotation</I>, <I>yrotation</I>, <I>lngref</I>, <I>latref</I>, 
  and <I>projection</I> parameters. If <I>Lngunits</I> and <I>latunits</I>
  are undefined they default to the values in the database or to
  the quantities "<TT>hours</TT>" and "<TT>degrees</TT>" respectively.
  If the <I>forward</I>
  parameter is "<TT>yes</TT>", the input coordinates are assumed to be pixel coordinates
  and are transformed to celestial coordinates. If <I>forward</I> is "<TT>no</TT>", then
  the input coordinates are assumed to be celestial coordinates and are
  transformed to pixel coordinates.
  <P>
  The transformation computed by CCMAP has the following form where x and y
  are the pixel coordinates and xi and eta are the corresponding standard
  coordinates in arcseconds per pixel. The standard coordinates are computed
  by applying the appropriate sky projection to the celestial coordinates.
  <P>
  <P>
  <PRE>
  	 xi = f (x, y)
  	eta = g (x, y)
  </PRE>
  <P>
  The functions f and g are either power series, Legendre, or Chebyshev
  polynomials whose order and region of validity were set by the user when
  CCMAP was run. The plate solution is arbitrary and does not correspond to
  any physically meaningful model. However the first order terms can be given
  the simple geometrical interpretation shown below.
  <P>
  <PRE>
  	  xi = a + b * x + c * y
  	 eta = d + e * x + f * y
  	   b = xmag * cos (xrotation)
  	   c = ymag * sin (yrotation)
  	   e = -xmag * sin (xrotation)
  	   f = ymag * cos (yrotation)
  	   a = xi0 - b * xref - c * yref = xshift
  	   d = eta0 - e * xref - f * yref = yshift
  	   xi0 = 0.0
  	   eta0 = 0.0
  </PRE>
  <P>
  xref, yref, xi0, and eta0 are the origins of the reference and output
  coordinate systems respectively. xi0 and eta0 are both 0.0 by default.
  xmag and ymag are the x and y scales in " / pixel, and xrotation and yrotation
  are the x and y axes rotation angles measured counter-clockwise from original
  x and y axes.
  <P>
  If the CCMAP database is undefined then CCTRAN computes a linear plate
  solution using the parameters <I>xref</I>, <I>yref</I>, <I>xmag</I>,
  <I>ymag</I>, <I>xrotation</I>, <I>yrotation</I>, <I>lngref</I>, <I>latref</I>,
  <I>lngunits</I>, <I>latunits</I> and <I>projection</I> as shown below. Note
  that in this case xrotation and yrotation are interpreted as the rotation
  of the coordinates not the rotation of the coordinate axes.
  <P>
  <PRE>
  	  xi = a + b * x + c * y
  	 eta = d + e * x + f * y
  	   b = xmag * cos (xrotation)
  	   c = -ymag * sin (yrotation)
  	   e = xmag * sin (xrotation)
  	   f = ymag * cos (yrotation)
  	   a = xi0 - b * xref - c * yref = xshift
  	   d = eta0 - e * xref - f * yref = yshift
  	   xi0 = 0.0
  	   eta0 = 0.0
  </PRE>
  <P>
  Linear plate solutions are evaluated in the forward and reverse sense
  using the appropriate IRAF mwcs system routines. Higher order plate
  solutions are evaluated in the forward sense using straight-forward
  evaluation of the polynomial terms, in the reverse sense by applying
  Newton's method to the plate solution.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Formats</H3>
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
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute the plate solution and evaluate the forward transformation for
  the following input coordinate list.
  <P>
  <PRE>
  cl&gt; type coords
  13:29:47.297  47:13:37.52  327.50  410.38
  13:29:37.406  47:09:09.18  465.50   62.10
  13:29:38.700  47:13:36.23  442.01  409.65
  13:29:55.424  47:10:05.15  224.35  131.20
  13:30:01.816  47:12:58.79  134.37  356.33
  <P>
  <P>
  cl&gt; ccmap coords coords.db xcol=3 ycol=4 lngcol=1 latcol=2 inter-
  Coords File: coords  Image: 
      Database: coords.db  Record: coords
  Refsystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  Insystem: j2000  Coordinates: equatorial FK5
      Equinox: J2000.000 Epoch: J2000.00000000 MJD: 51544.50000
  Coordinate mapping status
      Ra/Dec or Long/Lat fit rms: 0.229  0.241   (arcsec  arcsec)
  Coordinate mapping parameters
      Sky projection geometry: tan
      Reference point: 13:29:48.129  47:11:53.37  (hours  degrees)
      Reference point: 318.735  273.900  (pixels  pixels)
      X and Y scale: 0.764  0.767  (arcsec/pixel  arcsec/pixel)
      X and Y axis rotation: 179.110  358.958  (degrees  degrees)
  <P>
  <P>
  cl&gt; type coords.db
  # Mon 15:10:37 13-May-96
  begin   coords
          xrefmean        318.7460000000001
          yrefmean        273.9320000000001
          lngmean         13.49670238888889
          latmean         47.19815944444444
          coosystem       j2000
          projection      tan
          lngref          13.49670238888889
          latref          47.19815944444444
          lngunits        hours
          latunits        degrees
          xpixref         318.7352667484295
          ypixref         273.9002619912411
          geometry        general
          function        polynomial
          xishift         247.3577084680361
          etashift        -206.1795977453246
          xmag            0.7641733802338992
          ymag            0.7666917500560622
          xrotation       179.1101291109185
          yrotation       358.9582148846163
          wcsxirms        0.2288984454992771
          wcsetarms       0.2411034140453112
          xirms           0.2288984454992771
          etarms          0.2411034140453112
          surface1        11
                          3.      3.
                          2.      2.
                          2.      2.
                          0.      0.
                          134.3700000000001       134.3700000000001
                          465.5000000000002       465.5000000000002
                          62.1    62.1
                          410.3800000000001       410.3800000000001
                          247.3577084680361       -206.1795977453246
                          -0.7640812161068504     -0.011868034832272
                          -0.01393966623835092    0.7665650170136847
          surface2        0
  <P>
  <P>
  <P>
  cl&gt; cctran coords STDOUT coords.db coords xcol=3 ycol=4 lngformat=%0.3h \<BR>
  latformat=%0.2h
  13:29:47.297  47:13:37.52 13:29:47.284 47:13:37.89
  13:29:37.406  47:09:09.18 13:29:37.425 47:09:09.24
  13:29:38.700  47:13:36.23 13:29:38.696 47:13:35.95
  13:29:55.424  47:10:05.15 13:29:55.396 47:10:05.09
  13:30:01.816  47:12:58.79 13:30:01.842 47:12:58.70
  <P>
  cl&gt; cctran coords STDOUT coords.db coords xcol=1 ycol=2 forward-
  327.341   409.894  327.50  410.38
  465.751    62.023  465.50   62.10
  441.951   410.017  442.01  409.65
  223.970   131.272  224.35  131.20
  134.717   356.454  134.37  356.33
  </PRE>
  <P>
  Note that for the forward transformation the original ras and decs are in
  columns 1 and 2 and the computed ras and decs are in columns 3 and 4, but
  for the reverse transformation the original x and y values are in columns
  3 and 4 and the computed values are in columns 1 and 2.
  <P>
  <P>
  2. Use the previous plate solution to transform x and y values to
  ra and dec values and vice versa but enter the plate solution by hand.
  <P>
  <PRE>
  cl&gt; cctran coords STDOUT "" xcol=3 ycol=4 lngformat=%0.3h latformat=%0.2h \<BR>
  xref=318.735 yref=273.900 lngref=13:29:48.129 latref=47:11:53.37 \<BR>
  xmag=.764 ymag=.767 xrot=180.890 yrot=1.042
  13:29:47.297  47:13:37.52 13:29:47.285 47:13:37.93
  13:29:37.406  47:09:09.18 13:29:37.428 47:09:09.17
  13:29:38.700  47:13:36.23 13:29:38.698 47:13:35.99
  13:29:55.424  47:10:05.15 13:29:55.395 47:10:05.04
  13:30:01.816  47:12:58.79 13:30:01.839 47:12:58.72
  <P>
  cl&gt; cctran coords STDOUT "" xcol=1 ycol=2 xref=318.735 yref=273.900 \<BR>
  lngref=13:29:48.129 latref=47:11:53.37 xmag=.764 ymag=.767 \<BR>
  xrot=180.890 yrot=1.042 forward-
  327.347   409.845  327.50  410.38
  465.790    62.113  465.50   62.10
  441.983   409.968  442.01  409.65
  223.954   131.334  224.35  131.20
  134.680   356.426  134.37  356.33
  <P>
  </PRE>
  <P>
  Note that there are minor differences between examples 1 and 2 due to
  precision differences in the input, and that the angles input to cctran
  in example 2 are the coordinate rotation angles not the axes rotation angles
  as printed by ccmap. The different is exactly 180 degrees in both cases.
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccmap, ccsetwcs, finder.tastrom, skyctran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'FORMATS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
