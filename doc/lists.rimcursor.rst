.. _rimcursor:

rimcursor — Read the image display cursor (makes a list)
========================================================

**Package: lists**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rimcursor -- repeatedly read and return image cursor values
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rimcursor [image]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The name of the reference image to which coordinates should refer.
  This parameter will be queried only if <B>rimcursor</B> cannot obtain
  the reference image name by other means; e.g. when cursor reads are
  being performed using the image display, <B>rimcursor</B> will assume that
  <I>image</I> is the currently displayed image.
  </DD>
  </DL>
  <DL>
  <DT><B>wcs = "<TT>logical</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcs' Line='wcs = "logical"'>
  <DD>The world coordinate system (<I>wcs</I>) to be used for coordinate output.
  The following standard world systems are predefined.
  <DL>
  <DT><B>logical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='logical' Line='logical'>
  <DD>Logical coordinates are image pixel coordinates relative to the image currently
  being displayed.  This is what the raw cursor read returns, so by default,
  <B>rimcursor</B> merely passes back the raw image cursor coordinates as
  would be returned by "<TT>=imcur</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>physical</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>The physical coordinate system is invariant with respect to linear
  transformations of the physical image matrix.  For example, if the reference
  image was created by extracting a section of another image, the physical
  coordinates of an object in the reference image will be the pixel coordinates
  of the same object in the original image.  The physical coordinate system
  thus provides a consistent coordinate system (a given object always has the
  same coordinates) for all images, regardless of whether any user world
  coordinate systems have been defined.
  </DD>
  </DL>
  <DL>
  <DT><B>world</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>The "<TT>world</TT>" coordinate system is the <I>current default WCS</I>.
  The default world system is the system named by the environment variable
  <I>defwcs</I> if defined in the user environment and present in the reference
  image WCS description, else it is the first user WCS defined for the image
  (if any), else physical coordinates are returned.
  </DD>
  </DL>
  <P>
  In addition to these three reserved WCS names, the name of any user WCS
  defined for the reference image may be given.  A user world coordinate system
  may be any linear or nonlinear world system.
  </DD>
  </DL>
  <DL>
  <DT><B>wxformat = "<TT></TT>", wyformat = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wxformat' Line='wxformat = "", wyformat = ""'>
  <DD>The default output format for the x and y coordinates. If wxformat or wyformat
  are undefined, rimcursor uses formatting options stored with the WCS in the  
  image header. If the WCS formatting options are not defined in the image
  header, then rimcursor uses a default format.
  </DD>
  </DL>
  <DL>
  <DT><B>cursor = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>The source for image cursor input.  By default, the hardware image cursor
  is read.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The task <B>rimcursor</B> iteratively reads the image display cursor,
  writing the cursor values to the standard output.  The standard output
  may be redirected into a text file to generate a coordinate list for use
  as input to other tasks.  Any IRAF program which normally reads the image
  cursor interactively may be run taking input from a list prepared
  using <B>rimcursor</B>.
  <P>
  An image should be displayed on the image display device before running
  <B>rimcursor</B>, and the device set to display the desired frame.
  When the program is run, a loop is entered reading the image
  cursor until the end of file character (e.g., &lt;ctrl/d&gt; or &lt;ctrl/z&gt;) is typed.
  Each cursor read causes a line to be printed on the standard output, after
  which the cursor is again read.  Cursor values consist of two coordinates,
  a coordinate system identification (currently identifying the display
  frame), and the key or colon command typed to terminate the cursor read.
  Note this task does not return pixel value information, see <B>imexamine</B>
  for this purpose.
  <P>
  While the program is waiting for the cursor to be read, i.e. whenever
  the image cursor is blinking rapidly, the terminal is said to be in
  "<TT>cursor mode</TT>".  To read the cursor position, enter any key not
  recognized as a cursor mode command (currently there are no cursor mode
  commands for the image cursor so any character may be typed).
  The colon key returns to text
  input for a line of text terminated by a carriage return.  This is
  called a "<TT>colon command</TT>".  The actual character or colon command one
  types depends upon the program for which the list is intended.  If the
  program will use only the coordinates of the cursor any character may be
  typed, e.g., the space bar.  If the program uses the key value to
  determine what action to take, then you must type a specific key.
  <P>
  The X and Y coordinates of the cursor position and other information
  comprising the cursor value are printed on the standard output when the
  cursor is read.  To keep track of objects or features marked in a long
  set of cursor reads one may want to enable display marking if provided
  by the display device; e.g. the <B>imtool</B> display server.
  Other useful features, such as zoom, may be available in the display
  device also.
  <P>
  The coordinates returned by <B>rimcursor</B> depend on the type of
  world coordinate system chosen by parameter <I>wcs</I> and those defined
  by the reference image.  The default "<TT>logical</TT>" coordinates are the
  image pixel coordinates being displayed.  This is available for all
  images and may be required by other tasks which read the generated list.
  The "<TT>physical</TT>" coordinate system provides coordinates from the "<TT>original
  data image</TT>" irrespective of any linear transformations (such as image
  sections) used to generate the current image from the original data image.
  Coordinates in a user or application defined linear or nonlinear world
  coordinate system may be obtained by setting the <I>wcs</I> parameter to
  "<TT>world</TT>" for coordinate output in the default world system, or to the name
  of the specific world system for which coordinates are desired.
  An example of a world coordinate system for direct astronomical images
  is RA and DEC using the tangent (gnonomic) projection.
  <P>
  Coordinate transformations from the logical coordinates of image pixels
  as given by a raw image cursor read, to physical or world coordinates is
  performed by <B>rimcursor</B>.  This aspect of the task may be used
  to transform image pixel coordinate lists of x and y values, as produced
  by some tasks such as <B>apphot</B> or <B>daophot</B> into world
  coordinates by specifying cursor input from the file rather than the
  image display cursor.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Formats</H3>
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
  <P>
  </UL>
  <! EndSection:   'FORMATS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Interactively generate a starlist (file "<TT>starlist</TT>") to be used as input
  to another program, e.g., for digital photometry.
  <P>
  <PRE>
      cl&gt; display dev$pix 1	# display image in frame 1
      cl&gt; rimcursor &gt; starlist	# make the object list
  <P>
      At this point, the cursor loop is entered and the terminal
      is placed into cursor mode.  The positions are marked using
      the space bar.
  <P>
      space_bar		mark the position of the object
      space_bar		mark the position of another object
      
      &lt;ctrl/z&gt;		(EOF) terminates rimcursor
  </PRE>
  <P>
  Given the above command sequence, the output file "<TT>starlist</TT>" might
  contain the following cursor values.
  <P>
  <PRE>
      441. 410. 101 \040 
      208. 506. 101 \040 
      378. 68. 101 \040 
  </PRE>
  <P>
  2. Get world coordinates for the default world coordinate system.
  <P>
  <PRE>
      cl&gt; rimcur wcs=world
      12.13436 63.5565 101 \040
      12.13448 63.5529 101 \040
      12.13499 63.5588 101 \040
  </PRE>
  <P>
  Since there is no format information in the image header, the coordinates are
  decimal RA and DEC in degrees.
  <P>
  3. Output the RA and DEC coordinates for an image in sexagesimal degrees.
  <P>
  <PRE>
      cl&gt; rimcur wcs=world xformat=%12.2h yformat=%12.2h
      19:47:12.25 33:15:03.66
      19:43:12.10 33:14:38.06
      19:45:12.40 33:15:56.03
  </PRE>
  <P>
  4. Output the RA in sexagesimal hours and DEC in sexagesimal degrees for an
  image.
  <P>
  <PRE>
      cl&gt; rimcur wcs=world xformat=%12.2H yformat=%12.2h
      13:47:12.25 47:15:03.66
      13:47:12.10 47:15:38.06
      13:47:12.40 47:15:56.03
  </PRE>
  <P>
  5. Convert a list of pixel coordinates to world coordinates.
  <P>
  <PRE>
      cl&gt; rimcur obs001 wcs=world cursor=coordlist &gt;worldlist
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Notes</H3>
  <! BeginSection: 'NOTES'>
  <UL>
  Future plans call for implementation of cursor mode commands for image
  display cursors similar to those available for graphics cursors.
  </UL>
  <! EndSection:   'NOTES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rgcursor, cursors
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'FORMATS' 'EXAMPLES' 'NOTES' 'SEE ALSO'  >
  
