listpixels — Convert an image section into a list of pixels
===========================================================

**Package: imutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>listpixels (Apr92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>listpixels (Apr92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>listpixels</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  listpixels -- print the pixel values for a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  listpixels images
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Images or list of image sections whose pixels are to be printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcs">wcs = "<TT>logical</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "logical"'>
  <DD>The world coordinate system to be used for coordinate output. The following
  standard systems are defined.
  <DL>
  <DT><B><A NAME="l_logical">logical</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='logical' Line='logical'>
  <DD>Logical coordinates are image pixel coordinates relative to the input
  image. For example the pixel coordinates of the lower left corner
  of an image section will always be (1,1) in logical units regardless of
  their values in the original image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_physical">physical</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>Physical coordinates are image pixel coordinates with respect to the original
  image. For example the pixel coordinates of the lower left corner
  of an image section will be its coordinates in the original image,
  including the effects of any linear transformations done on that image.
  Physical coordinates are invariant with respect to transformations
  of the physical image matrix.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_world">world</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>World coordinates are image pixel coordinates with respect to the
  current default world coordinate system. For example in the case
  of spectra world coordinates would most likely be in angstroms.
  The default world coordinate system is the system named by the environment
  variable <I>defwcs</I> if defined in the user environment and present in
  the image world coordinate system description, else it is the first user
  world coordinate system defined for the image, else physical coordinates
  are returned.
  </DD>
  </DL>
  <P>
  In addition to these three reserved world coordinate system names, the names
  of any user world coordinate system defined for the image may be given.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_formats">formats = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='formats' Line='formats = ""'>
  <DD>The default output formats for the pixel coordinates, one format
  per axis, with the individual formats separated by whitespace .
  If formats are undefined, listpixels uses the formatting options
  stored with the WCS in the image header. If the WCS formatting options
  are not stored in the image header, then listpixels uses a default
  value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print a title line for each image whose pixels are to be listed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The pixel coordinates in the world coordinates system specified by
  <I>wcs</I> and using the formats specified by <I>formats</I> are
  printed on the standard output on the standard output followed by
  the pixel value.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_formats">FORMATS</A></H2>
  <! BeginSection: 'FORMATS'>
  <UL>
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
  %h	    format as nn:nn:nn.n
  %15h	    right justify nn:nn:nn.n in field of 15 characters
  %-15h	    left justify nn:nn:nn.n in a field of 15 characters
  %12.2h	    right justify nn:nn:nn.nn
  %-12.2h	    left justify nn:nn:nn.nn
      
  %H	    / by 15 and format as nn:nn:nn.n
  %15H	    / by 15 and right justify nn:nn:nn.n in field of 15 characters
  %-15H	    / by 15 and left justify nn:nn:nn.n in field of 15 characters
  %12.2H	    / by 15 and right justify nn:nn:nn.nn
  %-12.2H	    / by 15 and left justify nn:nn:nn.nn
  <P>
  \n          insert a newline
  </PRE>
  </UL>
  <! EndSection:   'FORMATS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the pixels of an image on the standard output.
  <P>
  <PRE>
  	cl&gt; listpix m81
  </PRE>
  <P>
  2. List a subraster of the above image in logical coordinates.
  <P>
  <PRE>
  	cl&gt; listpix m81[51:55,151:155]
  	    1. 1. ...
  	    2. 1. ...
  	    3. 1. ...
  	    4. 1. ...
  	    5. 1. ...
  	    1. 2. ...
  	    .. .. ...
  </PRE>
  <P>
  3. List the same subraster in physical coordinates.
  <P>
  <PRE>
  	cl&gt; listpix m81[51:55,151:155] wcs=physical
  	    51. 151. ...
  	    52. 151. ...
  	    53. 151. ...
  	    54. 151. ...
  	    55. 151. ...
  	    51. 152. ...
  	    ... .... ...
  </PRE>
  <P>
  4. List a spectrum that has been dispersion corrected in angstrom units.
  <P>
  <PRE>
  	cl&gt; listpix n7027 wcs=world
  </PRE>
  <P>
  5. List the RA and DEC coordinates in hms and dms format and pixels value
  for an image section where axis 1 is RA and axis 2 is DEC.
  <P>
  <PRE>
  	cl&gt; listpix m51 wcs=world formats="%H %h"
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
  imheader, imgets, imhistogram
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'FORMATS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>