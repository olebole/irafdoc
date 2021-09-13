.. _wcsxymatch:

wcsxymatch — Generate matched pixel lists using the image wcs
=============================================================

**Package: immatch**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  wcsxymatch -- match input and reference image x-y coordinates using the WCS
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  wcsxymatch input reference output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images containing the input wcs.
  </DD>
  </DL>
  <DL>
  <DT><B>reference</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>The list of reference images containing the reference wcs. The number of
  reference images must be one or equal to the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output matched coordinate lists containing:
  1) the logical x-y pixel coordinates of a point
  in the reference image in columns 1 and 2, 2) the logical x-y pixel
  coordinates of the same point in the input image in columns 3 and 4,
  3) the world coordinates of the point in the reference and input
  image in columns 5 and 6. The output coordinate list can be
  input directly to the geomap task. The number of output files must be 
  equal to the number of input images or be the standard output STDOUT.
  </DD>
  </DL>
  <DL>
  <DT><B>coords = "<TT>grid</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coords' Line='coords = "grid"'>
  <DD>The source of the coordinate list. The options are:
  <DL>
  <DT><B>grid    </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='grid' Line='grid    '>
  <DD>Generate a list of <I>nx * ny</I> coordinates, evenly spaced over
  the reference image, and beginning and ending at logical coordinates
  <I>xmin</I> and <I>xmax</I> in x and <I>ymin</I> and <I>ymax</I> in y.
  </DD>
  </DL>
  <DL>
  <DT><B>&lt;filename&gt;</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='&lt;filename&gt;'>
  <DD>The name of the text file containing the world coordinates of a set of
  points in the reference image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF'>
  <DD>The minimum and maximum logical x and logical y coordinates used to generate
  the grid of control points if <I>coords</I> = "<TT>grid</TT>". Xmin, xmax, ymin, and
  ymax default to 1, the number of columns in the reference image, 1, and the
  number of lines in the reference image, respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>nx = 10, ny = 10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nx' Line='nx = 10, ny = 10'>
  <DD>The number of points in x and y used to generate the coordinate grid
  if <I>coords</I> = "<TT>grid</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>wcs = "<TT>world</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "world"'>
  <DD>The world coordinate system of the coordinates.  The options are:
  <DL>
  <DT><B>physical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>Physical coordinates are pixel coordinates which are invariant with
  respect to linear transformations of the physical image data.  For example,
  if the reference 
  image is a rotated section of a larger input image, the physical
  coordinates of an object in the reference image are equal to the physical
  coordinates of the same object in the input image, although the logical
  pixel coordinates are different.
  </DD>
  </DL>
  <DL>
  <DT><B>world</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>World coordinates are image coordinates which are invariant with
  respect to linear transformations of the physical image data and which
  are in world units, normally decimal degrees for sky projection coordinate
  systems and angstroms for spectral coordinate systems. Obviously if the
  wcs is correct the ra and dec or wavelength and position of an object
  should remain the same not matter how the image
  is linearly transformed. The default world coordinate
  system is either 1) the value of the environment variable "<TT>defwcs</TT>" if
  set in the user's IRAF environment (normally it is undefined) and present
  in the image header, 2) the value of the "<TT>system</TT>"
  attribute in the image header keyword WAT0_001 if present in the
  image header or, 3) the "<TT>physical</TT>" coordinate system.
  Care must be taken that the wcs of the input and
  reference images are compatible, e.g. it makes no sense to
  match the coordinates of a 2D sky projection and a 2D spectral wcs.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>transpose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transpose' Line='transpose = no'>
  <DD>Force a transpose of the reference image world coordinates before evaluating
  the world to logical coordinate transformation for the input image ? This
  option is useful if there is not enough information in the reference and
  input image headers to tell whether or not the images are transposed with
  respect to each other.
  </DD>
  </DL>
  <DL>
  <DT><B>xcolumn = 1, ycolumn = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xcolumn' Line='xcolumn = 1, ycolumn = 2'>
  <DD>The columns in the input coordinate list containing the x and y coordinate
  values if <I>coords</I> = &lt;filename&gt;.
  </DD>
  </DL>
  <DL>
  <DT><B>xunits = "<TT></TT>", ls yunits = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xunits' Line='xunits = "", ls yunits = ""'>
  <DD>The units of the x and y coordinates in the input coordinate list 
  if <I>coords</I> = &lt;filename&gt;, by default decimal degrees for sky projection 
  coordinate systems, otherwise any units.
  The options are:
  <DL>
  <DT><B>hours</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='hours' Line='hours'>
  <DD>Input coordinates specified in hours are converted to decimal degrees by
  multiplying by 15.0.
  </DD>
  </DL>
  <DL>
  <DT><B>native</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='native' Line='native'>
  <DD>The internal units of the wcs. No conversions on the input coordinates
  are performed.
  </DD>
  </DL>
  <P>
  If the units are not specified the default is "<TT>native</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>xformat = "<TT>%10.3f</TT>", yformat = "<TT>%10.3f</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xformat' Line='xformat = "%10.3f", yformat = "%10.3f"'>
  <DD>The format of the output logical x and y reference and input pixel
  coordinates in columns 1 and 2 and 3 and 4 respectively. By default the
  coordinates are output right justified in a field of ten spaces with
  3 digits following the decimal point. 
  </DD>
  </DL>
  <DL>
  <DT><B>wxformat = "<TT></TT>", wyformat = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wxformat' Line='wxformat = "", wyformat = ""'>
  <DD>The format of the output world x and y reference and input image coordinates
  in columns 5 and 6 respectively. The internal default formats will give
  reasonable output formats and precision for both sky projection coordinates
  and other types, e.g. spectral coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>min_sigdigits = 7</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='min_sigdigits' Line='min_sigdigits = 7'>
  <DD>The minimum precision of the output coordinates if, the formatting parameters
  are undefined, or the output world coordinate system is "<TT>world</TT>" and the wcs
  format attribute is undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about the progress of the task.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  WCSXYMATCH matches the logical x and y pixel coordinates of a set of points 
  in the input image <I>input</I> with the logical x and y pixels coordinates
  of the same points in the reference image <I>reference</I>
  using world coordinate information
  in the respective image headers, and writes the results to a coordinate file
  <I>output</I>  suitable for input to the GEOMAP task.
  The input and reference images may be 1D or 2D but must both have
  the same dimensionality.
  <P>
  If <I>coords</I> = "<TT>grid</TT>", WCSXYMATCH computes a grid of <I>nx * ny</I> 
  logical x and y pixel coordinates evenly distributed over the 
  logical pixel space of the reference image as defined by the
  <I>xmin</I>, <I>xmax</I>, <I>ymin</I>, <I>ymax</I> parameters.
  The logical x and y pixel reference image coordinates are transformed to the
  world coordinate system defined by <I>wcs</I> using
  world coordinate information stored in the reference image header.
  The world coordinates are then transformed back to the logical x and y pixel
  input image coordinates, using world coordinate system information stored in
  the input image header. 
  <P>
  If <I>coords</I> is a file name, WCSXYMATCH reads a list of x and y 
  reference image world coordinates from columns <I>xcolumn</I> and <I>ycolumn</I>
  in the input coordinates file,  and transforms these coordinates to
  "<TT>native</TT>" coordinate units using the <I>xunits</I> and <I>yunits</I> parameters.
  The reference image world coordinates are
  transformed to logical reference and input image coordinates
  using the value of the <I>wcs</I> parameter and world coordinate
  information in the reference and input image headers.
  <P>
  WCSXYMATCH will terminate with an error if the reference and input images
  are not both either 1D or 2D.
  If the world coordinate system information cannot be read from either
  the reference or input image header, the requested transformations
  from the world &lt;-&gt; logical coordinate systems cannot be compiled for either
  or both images, or the world coordinate systems of the reference and input
  images are fundamentally incompatible in some way, the output logical
  reference and input image coordinates are both set to a grid of points
  spanning the logical pixel space of the input, not the reference image,
  and defining an identify transformation, is written to the output file.
  <P>
  The computed reference and input logical coordinates and the
  world coordinates are written to the output file using
  the <I>xformat</I> and <I>yformat</I>, and the <I>wxformat</I> and <I>wxformat</I>
  parameters respectively. If these formats are undefined and, in the
  case of the world coordinates, a format attribute cannot be
  read from either the reference or the input images, the coordinates are
  output with the %g format and <I>min_sigdigits</I> of precision.
  <P>
  If the reference and input images are 1D then the 
  output logical and world y coordinates are
  set to 1.
  <P>
  If <I>verbose</I> is "<TT>yes</TT>" then a title section is written to the output
  file for each set of computed coordinates, along with messages about
  what if anything went wrong with the computation.
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
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  Additional  information  on  IRAF  world  coordinate  systems including
  more detailed descriptions of the "<TT>logical</TT>", "<TT>physical</TT>", and "<TT>world</TT>"
  coordinate systems can be
  found  in  the  help  pages  for  the  WCSEDIT  and  WCRESET  tasks. 
  Detailed   documentation   for  the  IRAF  world  coordinate  system 
  interface MWCS can be found in  the  file  "<TT>iraf$sys/mwcs/MWCS.hlp</TT>".
  This  file  can  be  formatted  and  printed  with the command "<TT>help
  iraf$sys/mwcs/MWCS.hlp fi+ | lprint</TT>".  Information on the spectral
  coordinates systems and their suitability for use with WCSXYMATCH
  can be obtained by typing "<TT>help specwcs | lprint</TT>".
  Details of  the  FITS  header
  world  coordinate  system  interface  can  be  found in the document
  "<TT>World Coordinate Systems Representations Within  the  FITS  Format</TT>"
  by Hanisch and Wells, available from our anonymous ftp archive.
      
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute a matched list of 100 logical x and y coordinates for an X-ray 
  and radio image of the same field, both of which have accurate sky
  projection world coordinate systems. Print the output world coordinates
  in hh:mm:ss.ss and dd:mm:ss.s format
  <P>
  <PRE>
  	cl&gt; wcsxymatch image refimage coords wxformat=%12.2H \<BR>
  	    wyformat=%12.1h
  </PRE>
  <P>
  2. Given a list of ras and decs of objects in the reference image,
  compute a list of matched logical x and y coordinates for the two images,
  both of which have a accurate sky projection wcss. The ras and decs are in
  columns 3 and 4 of the input coordinate file and are in hh:mm:ss.ss and
  dd:mm:ss.s format respectively. Print the output world coordinates
  in the same units as the input.
  <P>
  <PRE>
  	cl&gt; wcsxymatch image refimage coords coords=radecs \<BR>
  	    xcolumn=3 ycolumn=4 xunits=hours wxformat=%12.2H \<BR>
  	    wyformat=%12.1h
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  tprecess,wcstran,geomap,register,geotran,wcsmap,wregister
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'FORMATS' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
