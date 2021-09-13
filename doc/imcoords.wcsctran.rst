.. _wcsctran:

wcsctran — Transform coordinates from one iraf image wcs to another
===================================================================

**Package: imcoords**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  wcsctran -- use the image WCS to transform between IRAF coordinate systems
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  wcsctran input output image inwcs outwcs
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input coordinate files. The number of input coordinate
  files must be one or equal to the number of input images. Coordinates
  may be entered by hand by setting input to "<TT>STDIN</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The list of output coordinate files. The number of coordinate files
  must be one or equal to the number of input images. Results may be printed
  on the terminal by setting output to "<TT>STDOUT</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of input images containing the WCS information.
  </DD>
  </DL>
  <DL>
  <DT><B>inwcs, outwcs</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='inwcs' Line='inwcs, outwcs'>
  <DD>The input and output coordinate systems. Coordinates in the input
  file are assumed to be in the input system. Coordinates are written to
  the output file in the output system. The options are:
  <DL>
  <DT><B>logical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='logical' Line='logical'>
  <DD>Logical coordinates are pixel coordinates relative to the current
  image. The logical coordinate system is the coordinate system used by
  the image input/output routines to access the image data on disk.
  </DD>
  </DL>
  <DL>
  <DT><B>tv    </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='tv' Line='tv    '>
  <DD>Tv coordinates are pixel coordinates used by the ximtool and saoimage
  display servers.
  Tv coordinates include the effects of any input image section, but
  do not include the effects of previous linear transformations.
  If the input image name does not include an image section, then tv coordinates
  are identical to logical coordinates. If the input image name does include
  a section, and the input image has not been linearly transformed or 
  copied from a parent image, tv coordinates are identical to physical
  coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>physical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>Physical coordinates are pixel coordinates invariant with respect to linear
  transformations of the physical image data.  For example, if the current
  image was created by extracting a section of another image, the physical
  coordinates of an object in the current image will be equal to the physical
  coordinates of the same object in the parent image, although the logical
  coordinates will be different.
  </DD>
  </DL>
  <DL>
  <DT><B>world</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>World coordinates are image coordinates in any units which are invariant with
  respect to linear transformations of the physical image data. For example, 
  the ra and dec of an object will always be the same no matter how the image
  is linearly transformed. The default world coordinate
  system is either 1) the value of the environment variable "<TT>defwcs</TT>" if
  set in the user's IRAF environment (normally it is undefined) and present
  in the image header, 2) the value of the "<TT>system</TT>"
  attribute in the image header keyword WAT0_001 if present in the
  image header or, 3) the "<TT>physical</TT>" coordinate system.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>columns = "<TT>1 2 3 4 5 6 7</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='columns' Line='columns = "1 2 3 4 5 6 7"'>
  <DD>The list of columns separated by whitespace or commas in the input coordinate
  file containing the coordinate values.
  The number of specified columns must be greater than or equal to the
  dimensionality of the input image. The coordinates are read in the
  order they are specified in the columns parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>units = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='units' Line='units = ""'>
  <DD>The units of the input coordinate values, normally degrees for the sky
  projection coordinate systems and angstroms for spectral coordinate
  systems. 
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
  Units conversions are performed only if the input wcs is "<TT>world</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>formats = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='formats' Line='formats = ""'>
  <DD>The format for the computed output coordinates. If the formats
  parameter is undefined then: 1) the value of the wcs format attribute
  is used if the output wcs is "<TT>world</TT>" and the attribute is defined, 2)
  %g format is used with the precision set to the maximum of the precision of
  the input coordinates and the value of the min_sigdigits parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>min_sigdigits = 7</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='min_sigdigits' Line='min_sigdigits = 7'>
  <DD>The minimum precision of the output coordinates if, the formats parameter
  is undefined, and the output coordinate system is "<TT>world</TT>" but the wcs
  format attribute is undefined.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print comment lines to the output file as the task executes.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  WCSCTRAN transforms a list of coordinates, read from  the input file
  <I>input</I>, from the coordinate system defined by <I>inwcs</I> to the
  coordinate system defined by <I>outwcs</I> using world coordinate system
  information in the input image <I>image</I> header and writes the results
  to the output file <I>output</I>.
  <P>
  The input coordinates are read from and written to the
  columns in the input / output file specified by the <I>columns</I> parameter. 
  The units of the input coordinate units are assumed to be the internal
  units of the coordinate system as defined in the image header, normally
  degrees for sky projection coordinate systems and angstroms for
  spectral coordinate systems. For convenience input coordinates in hours
  are accepted and converted to decimal degrees if the <I>units</I> parameter
  is set appropriately.
  <P>
  The format of the output units can be set using the
  <I>formats</I> parameter. If the  output formats are unspecified then the
  output coordinates are written using, 1) the value of wcs format attribute if
  outwcs = "<TT>world</TT>" and the attribute is defined, or, 2) the %g format and a 
  precision which is the maximum of the precision of the input coordinates
  and the value of the <I>min_sigdigits</I> parameter. All remaining
  fields in the input file are copied to the output file without modification.
  <P>
  WCSCTRAN transforms coordinates from one builtin IRAF coordinate system
  to another.  The builtin coordinate systems are "<TT>logical</TT>", "<TT>physical</TT>", and
  "<TT>world</TT>". For convenience WCSCTRAN also supports the "<TT>tv</TT>" coordinate system
  which is not a builtin IRAF system, but is used by the display server tasks
  XIMTOOL, SAOIMAGE, and IMTOOL.
  <P>
  The <I>logical coordinate system</I> is the pixel coordinate system of the
  current image. This coordinate system is the one used by the image
  input/output routines to access the image on disk. In the
  logical coordinate system,
  the coordinates of the pixel centers must lie within the following
  range: 1.0 &lt;= x[i] &lt;= nx[i], where x[i] is the coordinate in dimension i,
  nx[i] is the size of the image in dimension i, and the current maximum
  number of image dimensions is 7. In the case of an image section,
  the nx[i] refer to the dimensions of the section, not the dimensions
  of the full image.
  <P>
  The <I>tv coordinate system</I> is the pixel coordinate system used by the
  display servers XIMTOOL, SAOIMAGE, and IMTOOL. 
  For images which are not image sections
  the tv and logical coordinate systems are identical. For images which are
  image sections the tv and physical coordinate systems are identical if
  the image has not undergone any prior linear transformations such as
  axis flips, section copies, shifts, scale changes, rotations, etc.
  <P>
  The <I>physical coordinate system</I> is the coordinate system in which the
  pixel coordinates of an object are invariant to successive linear
  transformations
  of the image. In this coordinate system, the pixel coordinates of an object
  in an image remain the same, regardless of any section copies, shifts,
  rotations, etc on the image. For example, an object with the
  physical coordinates (x,y) in an image would still have physical 
  coordinates (x, y) in an image which is a section of the original image.
  <P>
  The <I>world coordinate system</I> is the default coordinate system for the
  image. The default world coordinate system is the one named by the
  environment variable "<TT>defwcs</TT>" if defined in the user environment (initially
  it is undefined) and present in the image header; else it is the first
  world coordinate system
  defined for the image (the .imh and .hhh image format support only one wcs
  but the .qp format can support more); else it is the physical coordinate
  system.
  <P>
  In most cases the number of input coordinates is equal to the number of
  output coordinates, and both are equal to the dimensions of the input image.
  In some cases however, the number of output coordinates may be greater or
  less than the number of input coordinates. This situation occurs
  if the input image has been dimensionally-reduced, i.e. is a section
  of a higher-dimensioned parent image, and the input coordinate system
  or the output coordinate system but not both is "<TT>logical</TT>" or "<TT>tv</TT>".
  For example, if the input image is a 1D line extracted from a 2D parent
  image with a sky projection world coordinate system, and the user
  specifies a transformation from the "<TT>logical</TT>" to "<TT>world</TT>" systems, 
  only one input coordinate (column number) is required, but two output
  coordinates (ra and dec) are produced. If the input and output coordinate
  systems are reversed, then two input coordinates (ra and dec) are required,
  but only one output coordinate (column number) is produced. If the number of
  output coordinates is less than the number of input coordinates, the extra
  input coordinate columns in the input file are set to INDEF in the output file.
  If the number of output columns is greater than the number of input columns,
  the extra coordinate columns are added to the end of the output line.
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
  <P>
  </UL>
  <! EndSection:   'FORMATS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  Additional information on IRAF world coordinate systems can be found in
  the help pages for the WCSEDIT and WCRESET tasks.
  Detailed documentation for the IRAF world coordinate system interface MWCS
  can be found in the file "<TT>iraf$sys/mwcs/MWCS.hlp</TT>". This file can be
  formatted and printed with the command "<TT>help iraf$sys/mwcs/MWCS.hlp fi+ |
  lprint</TT>".  Details of the FITS header world coordinate system interface can
  be found in the document "<TT>World Coordinate Systems Representations Within the
  FITS Format</TT>" by Hanisch and Wells, available from our anonymous ftp
  archive.
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Find the pixel coordinates of a list of objects in an image, given a list
  of their ras and decs in hh:mm:ss.s and dd:mm:ss format. Limit the precision
  of the output coordinates to 3 decimal places. In this example, the input
  ras and decs are assumed to be in columns 1 and 2 of the input coordinate
  file, and the ras must be converted from hours to decimal degrees.
  <P>
  <PRE>
  	im&gt; wcsctran incoords outcoords image world logical units="h n" \<BR>
  	    formats="%8.3f %0.3f"
  </PRE>
  <P>
  2. Repeat the previous example using the same input coordinate list to
  produce output coordinate lists for a list of input images.
  <P>
  <PRE>
  	im&gt; wcsctran incoords @outcoolist @imlist world logical units="h n" \<BR>
  	    formats="%8.3f %8.3f"
  </PRE>
  <P>
  3. Transform pixel coordinates in a photometry file to ra and dec
  coordinates, writing the output coordinates in hh:mm:ss.ss and dd:mm:ss.s
  format. The input pixel coordinates are stored in columns 3 and 4 of the
  input coordinate file.
  <P>
  <PRE>
  	im&gt; wcsctran magfile omagfile image logical world col="3 4" \<BR>
  	    formats="%12.2H %12.1h"
  </PRE>
  <P>
  4. Given a set of pixel coordinates in the parent image, find the pixel
  coordinates of the same objects in an image which is a shifted, rotated
  and scaled version of the parent image. The input coordinate list
  is created using the displayed parent image and the rimcursor task. 
  The output coordinate lists is marked on the displayed transformed 
  image using the tvmark task.
  <P>
  <PRE>
  	im&gt; display parent 1 fi+
  	im&gt; rimcursor &gt; coolist
  	im&gt; imlintran parent image 45.0 45.0 1.5 1.5 xin=256 yin=256 \<BR>
  	    xout=281 yout=263
  	im&gt; wcsctran coolist ocoolist image physical logical
  	im&gt; display image 2 fi+
  	im&gt; tvmark 2 outcoolist
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
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  wcsreset, wcsedit, rimcursor, listpixels, lintran
  <P>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'FORMATS' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
