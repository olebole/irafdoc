gregister — Register 1-D or 2-D images using the geomap transforms
==================================================================

**Package: immatch**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>gregister (Dec98)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.immatch</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>gregister (Dec98)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>gregister</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  gregister -- transform a list of images from one coordinate system to another
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  gregister input output database transforms
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be transformed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The name of the text file database produced by GEOMAP containing the coordinate
  transformation(s).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_transforms">transforms</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transforms' Line='transforms'>
  <DD>The list of the database record(s) containing the transformations. 
  The number of transforms must be 1 or the same as the number of input
  images.  Transforms is usually the name of the
  text file input to GEOMAP which lists the reference and input
  coordinates of the control points.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_geometry">geometry = "<TT>geometric</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='geometry' Line='geometry = "geometric"'>
  <DD>The type of geometry to be applied: The choices are:
  <DL>
  <DT><B><A NAME="l_linear">linear</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>The linear part, shifts, scales and rotations are computed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_geometric">geometric</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='geometric' Line='geometric'>
  <DD>The full transformation is computed.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xmin">xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF'>
  <DD>The minimum and maximum x and y reference values of the output image.
  Xmin, xmax, ymin and ymax default to minimum and maximum values set in GEOMAP,
  and may not extend beyond the bounds of those parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xscale">xscale = 1.0, yscale = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xscale' Line='xscale = 1.0, yscale = 1.0'>
  <DD>The output x and y scales in units of reference x and y
  units per pixel, e.g "/ pixel or Angstroms / pixel if the reference
  coordinates
  are arc-seconds or Angstroms. If the reference coordinates are in pixels
  then xscale and yscale should be 1.0 to preserve the scale of the reference
  image. The default is set for pixel coordinates.
  If xscale and yscale are undefined (INDEF), xscale and yscale default to the
  range of the reference coordinates over the range in pixels.
  Xscale and yscale override the values of ncols and nlines.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ncols">ncols = INDEF, nlines = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = INDEF, nlines = INDEF'>
  <DD>The number of columns and lines in the output image. Ncols and nlines default
  to the size of the input image. If xscale or yscale are defined ncols or nlines
  are overridden.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xsample">xsample = 1.0, ysample = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xsample' Line='xsample = 1.0, ysample = 1.0'>
  <DD>The coordinate surface subsampling factor. The coordinate surfaces are
  evaluated at every xsample-th pixel in x and every ysample-th pixel in y.
  Transformed coordinates  at intermediate pixel values are determined by
  bilinear interpolation in the coordinate surfaces.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interpolant">interpolant = "<TT>linear</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interpolant' Line='interpolant = "linear"'>
  <DD>The choices are the following.
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Nearest neighbor.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_linear">linear</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Bilinear interpolation in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_poly3">poly3</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly3' Line='poly3'>
  <DD>Third order polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_poly5">poly5</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly5' Line='poly5'>
  <DD>Fifth order polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_spline3">spline3</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>Bicubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sinc">sinc</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sinc' Line='sinc'>
  <DD>2D sinc interpolation. Users can specify the sinc interpolant width by
  appending a width value to the interpolant string, e.g. sinc51 specifies
  a 51 by 51 pixel wide sinc interpolant. The sinc width will be rounded up to
  the nearest odd number.  The default sinc width is 31 by 31.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lsinc">lsinc</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='lsinc' Line='lsinc'>
  <DD>Look-up table sinc interpolation. Users can specify the look-up table sinc
  interpolant width by appending a width value to the interpolant string, e.g.
  lsinc51 specifies a 51 by 51 pixel wide look-up table sinc interpolant. The user
  supplied sinc width will be rounded up to the nearest odd number. The default
  sinc width is 31 by 31 pixels. Users can specify the resolution of the lookup
  table sinc by appending the look-up table size in square brackets to the
  interpolant string, e.g. lsinc51[20] specifies a 20 by 20 element sinc
  look-up table interpolant with a pixel resolution of 0.05 pixels in x and y.
  The default look-up table size and resolution are 20 by 20 and 0.05 pixels
  in x and y respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_drizzle">drizzle</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='drizzle' Line='drizzle'>
  <DD>2D drizzle resampling. Users can specify the drizzle pixel fraction in x and y
  by appending a value between 0.0 and 1.0 in square brackets to the
  interpolant string, e.g. drizzle[0.5]. The default value is 1.0.
  The value 0.0 is increased internally to 0.001. Drizzle resampling
  with a pixel fraction of 1.0 in x and y is equivalent to fractional pixel
  rotated block summing (fluxconserve = yes) or averaging (flux_conserve = no)  if
  xmag and ymag are &gt; 1.0.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_boundary">boundary = "<TT>nearest</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The boundary extension choices are:
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reflect">reflect</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Generate value by reflecting about the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wrap">wrap</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Generate a value by wrapping around to the opposite side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>The value of the constant for boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fluxconserve">fluxconserve = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fluxconserve' Line='fluxconserve = yes'>
  <DD>Preserve the total image flux. The output pixel values are multiplied by
  the Jacobian of the coordinate transformation.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nxblock">nxblock = 512, nyblock = 512</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxblock' Line='nxblock = 512, nyblock = 512'>
  <DD>If the dimensions of the output image are less than nxblock and nyblock
  then the entire image is transformed at once. Otherwise blocks of size
  nxblock by nyblock are transformed one at a time.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about the progress of the task ?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  GREGISTER corrects an image for geometric distortion using the coordinate
  transformation computed by GEOMAP. The transformation is stored as the
  coefficients of a polynomial surface in record <I>transforms</I>,
  in the text file <I>database</I>.
  The coordinate surface is sampled at every <I>xsample</I> and <I>ysample</I>
  pixel in x and y.
  The transformed coordinates at intermediate pixel values are
  determined by bilinear interpolation in the coordinate surface. If
  <I>xsample</I> and <I>ysample</I> = 1, the coordinate
  surface is evaluated at every pixel. Use of <I>xsample</I> and <I>ysample</I>
  are strongly recommended for large images and high order coordinate
  surfaces in order to reduce the execution time.
  <P>
  <I>Xmin</I>, <I>xmax</I>, <I>ymin</I> and <I>ymax</I> define the range of
  reference coordinates represented in the output picture. These numbers
  default to the minimum and maximum x and y reference values used by GEOMAP,
  and may not exceed these values.
  The scale and size of the output picture is determined as follows.
  <P>
  <PRE>
  	ncols = ncols(input)
  	if (xscale == INDEF)
  	    xscale = (xmax - xmin ) / (ncols - 1)
  	else
  	    ncols = (xmax - xmin) / xscale + 1
  <P>
  	nlines = nlines(input)
  	if (yscale == INDEF)
  	    yscale = (ymax - ymin ) / (nlines - 1)
  	else
  	    nlines = (ymax - ymin) / yscale + 1
  </PRE>
  <P>
  The output image gray levels are determined by interpolating in the input
  image at the positions of the transformed output pixels. If the
  <I>fluxconserve</I> switch is set the output pixel values are multiplied by
  the Jacobian of the transformation.  GREGISTER uses the routines in the
  2-D interpolation package.
  <P>
  The output image is computed in <I>nxblock</I> by <I>nyblock</I> pixel sections.
  If possible users should set these numbers to values larger than the dimensions
  of the output image, in order to minimize the number of disk reads and writes
  required to compute the output image.  If this is not feasible and the image
  rotation is small users should set nxblock to be greater than the number of
  columns in the output image, and nyblock to be as large as machine memory
  will permit.
  <P>
  If the environment variable <I>nomwcs</I> is "<TT>no</TT>" then the world coordinate
  system of the input image is modified in the output image to reflect the
  effects of the <I>linear</I> portion of the registration operation.
  Support does not yet exist in the IRAF world coordinate system interface
  for the higher order distortion corrections that GREGISTER is capable
  of performing.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_timings">TIMINGS</A></H2>
  <! BeginSection: 'TIMINGS'>
  <UL>
  It requires approximately 70 and 290 cpu seconds to correct a 512 by 512
  square image for geometric distortion using a low order coordinate surface
  and bilinear and biquintic interpolation respectively (Vax 11/750 far).
  <P>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <DL>
  <DT><B><A NAME="l_1">1.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='1' Line='1.'>
  <DD>Transform an image to the reference coordinate system of a 512 by 512 pixel
  square image. The output image will have the same scale and size as the
  reference image if the reference coordinates are in pixels.
  <P>
  <PRE>
  cl&gt; geomap coords database 1.0 512.0 1.0 512.0
  cl&gt; gregister input output database coords
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_2">2.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='2' Line='2.'>
  <DD>Repeat the previous example but rescale the output image. The scale of the
  output image will be 2.5 reference units per pixel and its size will be
  determined by the xmin, xmax, ymin, ymax parameters (1.0, 512.0, 1.0, 512.0).
  <P>
  <PRE>
  cl&gt; geomap coords database 1.0 512.0 1.0 512.0
  cl&gt; gregister input output database coords xscale=2.5 yscale=2.5
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_3">3.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='3' Line='3.'>
  <DD>Correct an image for 3rd order geometric distortion using an output scale of 2
  reference units per pixel unit and bicubic spline interpolation with no flux
  correction. 
  <P>
  <PRE>
  cl&gt; geomap coords database 1.0 512.0 1.0 512.0 xxorder=4 xyorder=4 \<BR>
  xxterms=yes yxorder=4 yyorder=4 yxterms=yes
  cl&gt; gregister input output database coords xscale=2. yscale=2. \<BR>
  &gt;&gt;&gt; inter=spline3 flux-
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_4">4.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='4' Line='4.'>
  <DD>Transform three images using 3 different transformation records stored
  in the database file.
  <P>
  <PRE>
  cl&gt; geomap coord1,coord2,coord3 database 1. 512. 1. 512.
  cl&gt; gregister im1,im2,im3 imout1,imout2,imout3 database \<BR>
  &gt;&gt;&gt; coord1,coord2,coords3
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_5">5.</A></B></DT>
  <! Sec='EXAMPLES' Level=0 Label='5' Line='5.'>
  <DD>Repeat the above example using the textfiles inlist, outlist, reclist which
  contain the list of input images, list of output images and list of coordinate
  files respectively.
  <P>
  <PRE>
  cl&gt; geomap @reclist database 1. 512. 1. 512.
  cl&gt; gregister @inlist @outlist database @reclist
  </PRE>
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Support does yet exist in the IRAF world coordinate system interface
  for the higher order distortion corrections that GREGISTER is capable
  of performing.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imshift, magnify, rotate, imlintran, geomap, geotran, geoxytran
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'TIMINGS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>