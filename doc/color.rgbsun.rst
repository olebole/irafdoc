rgbsun — Create a Sun 24-bit RGB rasterfile
===========================================

**Package: color**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>rgbsun (Oct92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>color</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>rgbsun (Oct92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>rgbsun</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  rgbsun -- make a Sun 24-bit RGB rasterfile from three IRAF images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  rgbsun red green blue rgb
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_red">red, green, blue</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='red' Line='red, green, blue'>
  <DD>Input image names for the red, green, and blue components.  The images
  must all be two dimensional and of the same size.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rgb">rgb</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rgb' Line='rgb'>
  <DD>Output file name for the Sun 24-bit RGB rasterfile.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rz1">rz1, rz2, gz1, gz2, bz1, bz2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rz1' Line='rz1, rz2, gz1, gz2, bz1, bz2'>
  <DD>Range of values in the input images to be mapped to the minimum and maximum
  intensity in each color.  Image pixel values outside the range are mapped
  to the nearest endpoint.  The values correspond to the input image
  intensities even when using logarithmic mapping.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logmap">logmap = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logmap' Line='logmap = no'>
  <DD>Use logarithmic intensity mapping?  The logarithm of the input pixel
  values, in the range given by the z1 and z2 parameters, is taken before
  dividing the range into the 85 display levels.  Logarithmic mapping allows
  a greater dynamic range.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_swap">swap = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='swap' Line='swap = no'>
  <DD>Swap rasterfile bytes on output?  Used when rasterfiles are being written
  to a computer with opposite byte-swapping from that of the home computer
  (e.g. between VAX and Sun).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Rgbsun</B> takes three input IRAF images and produces a 24-bit Sun
  rasterfile.  Though this file type was developed by Sun Microcomputers it
  is a relatively simple format which may useful on other machines have
  software designed to use it.  The color image may be display with a variety
  of tools such as <B>xv</B> (a very powerful and generic, public domain
  viewer for X-window systems), <B>xloadimage</B> (another X-window display
  tool), <B>screenload</B> (a simple displayer on Sun computers), and
  <B>snapshot</B> (a Open-Look tool).  Also some color printers can be used
  with this format such as a Shinko color printer.
  <P>
  If one wants to display images which have a large dyanmic range it
  may be desirable to first take the logarithm of each image.  This may
  be done with the <I>logmap</I> parameter.  Other types of stretching may
  be accomplished by modifying the individual images first, say with
  <B>imfunction</B>.
  <P>
  If the output rasterfiles are being sent to a computer with opposite
  byte-swapping characteristics, set <I>swap</I> = yes (e.g., when running
  <B>rgbsun</B> on a VAX, with output to a Sun).
  <P>
  The rasterfile format produced is quite simple.  There is a header with 8
  integer values immediately followed by the data values.  The header has the
  following values of interest:
  <P>
  	Word 1:  Magic numer = 1504078485
  	Word 2:  The number of columns
  	Word 3:  The number of lines
  	Word 4:  The number of bits per pixel = 24
  <P>
  The data consists of triplets of 8-bit data values in the order blue,
  green, and red.  The triplet pixels are ordered by varying the column
  elements first and then the line elements.  The sequence is continuous
  except that each line is padded, if necessary, to maintain a multiple of 2
  bytes per line (with 3 bytes per pixel this means that images with an odd
  number of columns will have an extra zero byte).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Three 2048x2048 images of the Trifid nebula are obtained in the B, V,
  and R bandpasses.  These images are properly registered.  Examination of
  the histograms leads to selecting the display ranges 1-500 in each band.
  The image is then displayed on a workstation running an X-window system
  using the <B>xv</B> utility.  The file is also printed to a local
  color printer interfaced as a Unix printer (the Shinko at NOAO).
  <P>
  <PRE>
  	cl&gt; rgbsun trifidr trifidv trifidb trifid.ras \<BR>
  	&gt;&gt;&gt; rz1=1 rz2=500 gz1=1 gz2=500 bz1=1 bz2=500
  	cl&gt; !xv -swap24 trifid.ras
  	cl&gt; !lpr -Pclp trifd.ras
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  Example 1 takes 2:20 minutes (33 seconds CPU) on a SparcStation 2.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  rgbdither, rgbto8, color.package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>