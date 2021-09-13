.. _starfind:

starfind — Automatically detect stellar objects in a list of images
===================================================================

**Package: imcoords**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  starfind -- automatically detect stellar objects in a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  starfind image output hwhmpsf threshold
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of input images. The input images must be two-dimensional.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The list of output object files. The number of output files must equal the
  number of input images. If output is "<TT>default</TT>", or "<TT>dir$default</TT>", or a
  directory specification then a default name of the form
  dir$root.extension.version is constructed, where dir$ is the directory name,
  root is the root image name, extension is "<TT>obj</TT>", and version is the next
  available version number.
  </DD>
  </DL>
  <DL>
  <DT><B>hwhmpsf</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hwhmpsf' Line='hwhmpsf'>
  <DD>The half-width half-maximum of the image PSF in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>threshold</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold'>
  <DD>The detection threshold above local background in ADU.
  </DD>
  </DL>
  <DL>
  <DT><B>datamin = INDEF, datamax = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datamin' Line='datamin = INDEF, datamax = INDEF'>
  <DD>The minimum and maximum good data values in ADU. Datamin and datamax
  default to the constants -MAX_REAL and MAX_REAL respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>fradius = 2.5 (hwhmpsf)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fradius' Line='fradius = 2.5 (hwhmpsf)'>
  <DD>The fitting radius in units of hwhmpsf. Fradius defines the size
  of the Gaussian kernel used to compute the density enhancement image, and
  the size of the image region used to do the moment analysis.
  </DD>
  </DL>
  <DL>
  <DT><B>sepmin = 5.0 (hwhmpsf)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sepmin' Line='sepmin = 5.0 (hwhmpsf)'>
  <DD>The minimum separation for detected objects in units of hwhmpsf.
  </DD>
  </DL>
  <DL>
  <DT><B>npixmin = 5</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='npixmin' Line='npixmin = 5'>
  <DD>The minimum area of the detected objects in pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>maglo = INDEF, maghi = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maglo' Line='maglo = INDEF, maghi = INDEF'>
  <DD>The minimum and maximum magnitudes of the detected objects. Maglo and maghi
  default to the constants -MAX_REAL and MAX_REAL respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>roundlo = 0.0,  roundhi = 0.2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='roundlo' Line='roundlo = 0.0,  roundhi = 0.2'>
  <DD>The minimum and maximum ellipticity values of the detected objects, where
  ellipticity is defined as 1 - b / a, and a and b are the semi-major and
  semi-minor axis lengths respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>sharplo = 0.5, sharphi = 2.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sharplo' Line='sharplo = 0.5, sharphi = 2.0'>
  <DD>The minimum and maximum sharpness values of the detected objects, where
  sharpness is defined to be the ratio of the object size to the
  hwhmpsf parameter value.
  </DD>
  </DL>
  <DL>
  <DT><B>wcs = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = ""'>
  <DD>The world coordinate system.  The options are:
  <DL>
  <DT><B>"<TT>     </TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"     "'>
  <DD>The world coordinate system is undefined. Only logical (pixel) coordinates
  are printed.
  </DD>
  </DL>
  <DL>
  <DT><B>logical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='logical' Line='logical'>
  <DD>The world coordinate system is the same as the logical (pixel) coordinate
  system,  but two sets of identical logical (pixel) coordinates are printed.
  </DD>
  </DL>
  <DL>
  <DT><B>physical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>The world coordinate system is the same as the logical (pixel) coordinate
  system of the parent image if any.
  </DD>
  </DL>
  <DL>
  <DT><B>world</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>The world coordinate system of the image if any.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>wxformat = "<TT></TT>", wyformat = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wxformat' Line='wxformat = "", wyformat = ""'>
  <DD>The output format for the x and y axis world coordinates. If wxformat and
  wyformat are undefined then: 1) the value of the wcs format attribute is
  used if the output wcs is "<TT>world</TT>" and the attribute is defined, 2) "<TT>%9.3f</TT>"
  is used if the output wcs is "<TT>logical</TT>" or "<TT>physical</TT>", and "<TT>%11.8g</TT>" is used
  if the output wcs is "<TT>world</TT>". If the input image is a sky projection image and
  the x and y axes are ra and dec respectively, then the formats "<TT>%12.2H</TT>" and
  "<TT>%12.1h</TT>" will print the world coordinates in hours and degrees respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>boundary = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The boundary extension type. The choices are:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B>reflect</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Generate a value by reflecting around the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B>wrap</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Generate a value by wrapping around to the other side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.0'>
  <DD>The constant for constant boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B>nxblock = INDEF, nyblock = 256</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxblock' Line='nxblock = INDEF, nyblock = 256'>
  <DD>The working block size. If undefined nxblock and nyblock default
  to the number of columns and rows in the input image respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print messages about the progress of the task ?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  STARFIND searches the input images <I>image</I> for local density maxima
  with half-widths at half-maxima of ~ <I>hwhmpsf</I> and peak amplitudes
  greater than ~ <I>threshold</I> above the local background, and writes
  the list of detected objects to <I>output</I>.
  <P>
  STARFIND is a modified version of the DAOPHOT package DAOFIND algorithm.
  However STARFIND is intended for use with the IMAGES package image matching
  and image coordinates tasks and is therefore configured somewhat differently
  than the version used in the photometry packages.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Algorithms</H3>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  STARFIND assumes that the point spread function can be approximated by a radial
  Gaussian function whose sigma is 0.84932 * <I>hwhmpsf</I> pixels. STARFIND uses
  this model to construct a convolution kernel which is truncated at
  max (2.0, <I>fradius * hwhmpsf</I>) pixels and normalized to zero power.
  <P>
  For each point in the image density enhancement values are computed by
  convolving the input image with the radial Gaussian function. This operation
  is mathematically equivalent to fitting the image data at each point, in the
  least-squares sense, with a truncated, lowered, radial Gaussian function.
  After the convolution each density enhancement value is an estimate of
  the amplitude of the best fitting radial Gaussian function at that point.
  If <I>datamin</I> and <I>datamax</I> are defined then bad data is ignored,
  i.e. rejected from the fit, during the computation of the density enhancement
  values. Out of bounds image pixels are evaluated using the boundary extension
  algorithm parameters <I>boundary</I> and <I>constant</I>. Out of
  bounds density enhancement values are set to zero.
  <P>
  After the convolution, STARFIND steps through the density enhancement
  image searching for density enhancements greater then <I>threshold</I>
  and brighter than any density enhancements within a radius of
  <I>sepmin * hwhmpsf</I> pixels. For each potential detection the
  local background is estimated and used, along with the values of
  <I>datamin</I> and <I>datamax</I>, to estimate the position (Xc and Yc),
  size (Area and Hwhm), shape (E and Sharp), orientation (Pa), and
  brightness (Mag) of each object using the second order moments analysis
  shown below.
  <P>
  <PRE>
     I0 = sum (I)
      N = sum (1.0)
      if (N &lt;= 0)
          Sky = maxdata - maxden
      else
          Sky = I0 / N
  <P>
     M0 = sum (I - Sky)
     Mx = sum (X * (I - Sky))
     My = sum (Y * (I - Sky))
  <P>
     Xc = Mx / M0
     Xc = My / M0
    Mag = -2.5 * log10 (M0)
   Area = N
  <P>
    Mxx = sum ((X - Xc) * (X - Xc) * (I - Sky))
    Mxy = sum ((X - Xc) * (Y - Yc) * (I - Sky))
    Myy = sum ((Y - Yc) * (Y - Yc) * (I - Sky))
  <P>
   Hwhm = sqrt (log (2) * (Mxx + Myy))
      E = sqrt ((Mxx - Myy) ** 2 + 4 * Mxy ** 2) / (Mxx + Myy))
     Pa = 0.5 * atan (2 * Mxy / (Mxx - Myy))
  Sharp = Hmhw / Hwhmpsf 
  </PRE>
  <P>
  The sums are computed using pixels which lie within <I>fradius * hwhmpsf</I> of
  the maximum density enhancement, and whose values are within the good data
  limits defined by <I>datamin</I> and <I>datamax</I>, and which are above the local
  background estimate (Sky).
  <P>
  Objects whose magnitude, roundness, and sharpness characteristics are outside
  the values defined by <I>maglo</I>, <I>maghi</I>, <I>roundlo</I>, <I>roundhi</I>,
  <I>sharplo</I>, and <I>sharphi</I> and whose total areas is less than
  <I>npixmin</I> pixels are rejected from the list.
  <P>
  If <I>wcs</I> parameter is defined, the world coordinates as well as
  the pixel coordinates of the detected objects are computed and printed
  using the formats defined by <I>wxformat</I> and <I>wyformat</I>.
  <P>
  To minimize the memory requirements and increase efficiency, STARFIND
  is configured to operate on data blocks that are <I>nxblock * nyblock</I>
  in size. To keep the image i/o operation to a minimum nxblock is set
  to INDEF and defaults to the number of columns in the input image.
  Setting both parameter to INDEF will force STARFIND to perform the
  whole operation in memory.
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H3>Formats</H3>
  <! BeginSection: 'FORMATS'>
  <UL>
  <P>
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
   absent, 0      use as much space as needed (D field sets precision)
   
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
  1. Find stellar objects with peak values greater than 100 counts above
  local background in the test image dev$wpix whose fwhm is ~2.5 pixels.
  <P>
  <PRE>
  cl&gt; starfind dev$wpix default 1.25 100.
  cl&gt; display dev$wpix 1 fi+
  cl&gt; tvmark 1 wpix.obj.1 col=204 
  </PRE>
  <P>
  2. Repeat the previous example but tell starfind to compute and print
  world coordinates in hours and degrees as well as pixel coordinates.
  <P>
  <PRE>
  cl&gt; starfind dev$wpix default 1.25 100. wcs=world wxf="%12.2H"\<BR>
      wyf="%12.1h"
  cl&gt; display dev$wpix 1 fi+
  cl&gt; tvmark 1 wpix.obj.1 col=204 
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  Starfind requires approximately 8 CPU seconds to search a 512 by  512
  image  using  a   7 by 7 pixel convolution kernel (SPARCStation2).
  		
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
  imcentroid, apphot.daofind, daophot.daofind
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'ALGORITHMS' 'FORMATS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
