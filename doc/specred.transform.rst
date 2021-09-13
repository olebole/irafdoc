transform — Resample longslit spectra
=====================================

**Package: specred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>transform (Sep87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.twodspec.longslit</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>transform (Sep87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>transform</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  transform -- Transform longslit images to user coordinates
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  transform input output fitnames
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input images to be transformed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images.  The number of output images in the list must
  match the number of input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_minput">minput = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minput' Line='minput = ""'>
  <DD>List of input masks or references.  This mask is used to create an output
  mask and is currently not used in the calculation of the output pixel
  values.  The list may be empty, a single element to apply to all input
  images, or a list that matches the input list.  A element in the list
  may be "<TT>BPM</TT>" to use the mask referenced by the standard bad pixel mask
  keyword "<TT>BPM</TT>", "<TT>!&lt;keyword&gt;</TT>" to use another header keyword pointing to a
  mask, or a mask filename.  The mask file is typically a pixel list file
  but it may also be an image.  The mask values are interpreted as zero and
  greater than zero with the actual values ignored.  The mask is assumed to
  be registered with the input and no coordinate system matching is used.
  The mask maybe smaller or larger than the input image with non-overlapping
  pixels ignored and missing pixels assumed to be zero valued.  The mask
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_moutput">moutput = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='moutput' Line='moutput = ""'>
  <DD>List of output masks to be created.  The list may be empty or must match
  the input list.  Output masks may be specified even if no input mask is
  specified, in which case the output mask will identify pixels which map
  to regions outside the input images (also see the <I>blank</I> parameter).
  If an explicit extension is not specified a FITS mask is extension is
  created unless the environment variable "<TT>masktype</TT>" is set to "<TT>pl</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fitnames">fitnames  </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitnames' Line='fitnames  '>
  <DD>Names of the user coordinate maps in the database to be used in the transform.
  If no names are specified, using the null string "<TT></TT>", the world coordinate
  system (WCS) of the image is used.  This latter case may be used to
  resample previously WCS calibrated images to a different linear range
  or sampling.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database = "<TT>database</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "database"'>
  <DD>Database containing the coordinate map to be used in transforming the images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interptype">interptype = "<TT>spline3</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interptype' Line='interptype = "spline3"'>
  <DD>Image interpolation type.  The allowed types are "<TT>nearest</TT>" (nearest neighbor),
  "<TT>linear</TT>" (bilinear), "<TT>poly3</TT>" (bicubic polynomial), "<TT>poly5</TT>" (biquintic
  polynomial), and "<TT>spline3</TT>" (bicubic polynomial).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_flux">flux = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flux' Line='flux = yes'>
  <DD>Conserve flux per pixel?  If "<TT>no</TT>" then each output pixel is simply interpolated
  from the input image.  If "<TT>yes</TT>" the interpolated output pixel value is
  multiplied by the Jacobean of the transformation (essentially the ratio of
  pixel areas between the output and input images).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_x1">x1 = INDEF, y1 = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x1' Line='x1 = INDEF, y1 = INDEF'>
  <DD>User coordinates of the first output column and line.  If INDEF then the
  smallest value corresponding to a pixel from the image used to create the
  coordinate map is used.  These values are in user units regardless of whether
  logarithmic intervals are specified or not.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_x2">x2 = INDEF, y2 = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='x2' Line='x2 = INDEF, y2 = INDEF'>
  <DD>User coordinates of the last output column and line.  If INDEF then the
  largest value corresponding to a pixel from the image used to create the
  coordinate map is used.  These values are in user units regardless of whether
  logarithmic intervals are specified or not.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dx">dx = INDEF, dy = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dx' Line='dx = INDEF, dy = INDEF'>
  <DD>Output pixel intervals.  If INDEF then the interval is set to yield the
  specified number of pixels.  Note that for logarithmic intervals the
  interval must be specified as a base 10 logarithm (base 10) and not in
  user units.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nx">nx = INDEF, ny = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nx' Line='nx = INDEF, ny = INDEF'>
  <DD>Number of output pixels.  If INDEF and if the pixel interval is also INDEF then
  the number of output pixels is equal to the number of input pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xlog">xlog = no, ylog = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xlog' Line='xlog = no, ylog = no'>
  <DD>Convert to logarithmic intervals?  If "<TT>yes</TT>" the output pixel intervals
  are logarithmic.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_blank">blank = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blank' Line='blank = INDEF'>
  <DD>Value to put in the output transformed image when it transforms to regions
  outside the input image.  The special value INDEF will use the nearest
  input pixel which is the behavior before the addition of this parameter.
  Using special blank values allows other software to identify such out
  of input pixels.  See also the <I>moutput</I> parameter to identify
  out of input pixels in pixel masks.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfiles">logfiles = "<TT>STDOUT,logfile</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfiles' Line='logfiles = "STDOUT,logfile"'>
  <DD>List of files in which to keep a log.  If null, "<TT></TT>", then no log is kept.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The coordinate maps U(X,Y) and V(X,Y), created by the task <B>fitcoords</B>,
  are read from the specified database coordinate fits or from the
  world coordinate system (WCS) of the image.  X and Y are the original
  untransformed pixel coordinates and U and V are the desired output user or
  world coordinates (i.e. slit position and wavelength).  If a coordinate map
  for only one of the user coordinates is given then a one-to-one mapping
  is assumed for the other such that U=X or V=Y.  The coordinate maps are
  inverted to obtain X(U,V) and Y(U,V) on an even subsampled grid of U and
  V over the desired output image coordinates.  The X and Y at each output
  U and V used to interpolate from the input image are found by linear
  interpolation over this grid.  X(U,V) and Y(U,V) are not determined at
  every output point because this is quite slow and is not necessary since
  the coordinate surfaces are relatively slowly varying over the subsampling
  (every 10th output point).
  <P>
  The type of image interpolation is
  selected by the user.  Note that the more accurate the interpolator the
  longer the transformation time required.  The parameter <I>flux</I> selects
  between direct image interpolation and a flux conserving interpolation.
  Flux conservation consists of multiplying the interpolated pixel value by
  the Jacobean of the transformation at that point.  This is essentially
  the ratio of the pixel areas between the output and input images.  Note
  that this is not exact since it is not an integral over the output pixel.
  However, it will be very close except when the output pixel size is much
  greater than the input pixel size.  A log describing the image transformations
  may be kept or printed on the standard output.
  <P>
  The output coordinate grid may be defined by the user or allowed to
  default to an image of the same size as the input image spanning the
  full range of user coordinates in the coordinate transformation maps.
  When the coordinate maps are created by the task <B>fitcoords</B> the
  user coordinates at the corners of the image are recorded in the
  database.  By default these values are used to set the limits of the
  output grid.  If a pixel interval is not specified then an interval
  yielding the specified number of pixels is used.  The default number of
  pixels is that of the input image.  Note that if a pixel interval is
  specified then it takes precedence over the number of pixels.
  <P>
  The pixel intervals may also be logarithmic if the parameter <I>xlog</I> or
  <I>ylog</I> is "<TT>yes</TT>".  Generally, the number of output pixels is specified
  in this case .  However, if the interval is specified it must be a base
  10 logarithmic interval and not in units of the x and y limits which are
  specified in user units.
  <P>
  The transformation from the desired output pixel to the input image may
  fall outside of the input image.  In this case the output pixel may be
  set to the nearest pixel value in the input image or to a particular value
  using the <I>blank</I> parameter.  Also if an output mask is created this
  pixels will have a value of one in the mask.
  <P>
  The parameters <I>minput</I> and <I>moutput</I> provide for input and output
  pixel masks.  An input mask is not used in calculating the transformed
  pixel value but is used to identify the output pixels in the output mask
  which make a significant contribution to the interpolated value.  The
  significance is determined as follows.  The input mask values above zero
  are converted to one hundred.  The mask is then interpolated in the same
  way as the input image.  Any interpolated value of ten or greater is then
  given the value one in the output mask.  This means if all the input pixels
  had mask values of zero a result of zero means no bad pixels were used.
  If all the input pixels had values of 100 then the result will be 100 and
  the output mask will flag this as a bad pixel.  Other values are produced
  by a mixture of good and bad pixels weighted by the interpolation kernel.
  The choice of 10% is purely empirical and gives an approximate identification
  of significant affected pixels.
  zero and
  is created with values of 100
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Arc calibration images were used to determine a two dimensional dispersion
  map called dispmap.  Stellar spectra were used to determine a two dimensional
  distortion map call distort.  These maps where made using the task
  <B>fitcoords</B>. To transform a set of input images into linear wavelength
  between 3800 and 6400 Angstroms (the user coordinate units) with a dispersion
  of 3 Angstroms per pixel:
  <P>
  <PRE>
  	cl&gt; transform obj001,obj002 out001,out002 dispmap,distort \<BR>
  	&gt;&gt;&gt; y1=3800 y2=6400 dy=3
  </PRE>
  <P>
  To use logarithmic intervals in the wavelength to yield the same number of
  pixels in the output images as in the input images:
  <P>
  <PRE>
  	cl&gt; transform obj001,obj002 out001,out002 dispmap,distort \<BR>
  	&gt;&gt;&gt; y1=3800 y2=6400 ylog=yes
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_timings">TIMINGS</A></H2>
  <! BeginSection: 'TIMINGS'>
  <UL>
  The following timings were obtained for transforming a 511x512 real
  image to another 511x512 real image using two Chebyshev transformation
  surface functions (one for the dispersion axis, "<TT>henear</TT>", and one in
  spatial axis, "<TT>object</TT>") of order 6 in both dimensions created with the
  task <B>fitcoords</B>.  The times are for a UNIX/VAX 11/750.
  <P>
  <PRE>
  cl&gt; $transform input output henear,object interp=linear
  TIME (transform)  173.73  5:13  55%
  cl&gt; $transform input output henear,object interp=poly3
  TIME (transform)  266.63  9:17  42%
  cl&gt; $transform input output henear,object interp=spline3
  TIME (transform)  309.05  6:11  83%
  cl&gt; $transform input output henear,object interp=spline3
  TIME (transform)  444.13  9:44  76%
  cl&gt; $transform input output henear interp=linear
  TIME (transform)  171.32  7:24  38%
  cl&gt; $transform input output henear interp=spline3
  TIME (transform)  303.40  12:17  41%
  cl&gt; $transform input output henear,object interp=spline3 flux=no
  TIME (transform)  262.42  10:42  40%
  </PRE>
  <P>
  The majority of the time is due to the image interpolation and not evaluating
  the transformation functions as indicated by the last three examples.
  </UL>
  <! EndSection:   'TIMINGS'>
  <H2><A NAME="s_notes">NOTES</A></H2>
  <! BeginSection: 'NOTES'>
  <UL>
  <DL>
  <DT><B><A NAME="l_TRANSFORM">TRANSFORM: V2.12.2</A></B></DT>
  <! Sec='NOTES' Level=0 Label='TRANSFORM' Line='TRANSFORM: V2.12.2'>
  <DD>The use of bad pixel masks, a specified "<TT>blank</TT>" value, and use of a WCS
  to resample a WCS calibrated image was added.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_TRANSFORM">TRANSFORM: V2.6</A></B></DT>
  <! Sec='NOTES' Level=0 Label='TRANSFORM' Line='TRANSFORM: V2.6'>
  <DD>With Version 2.6 of IRAF the algorithm used to invert the user
  coordinate surfaces, U(X,Y) and V(X,Y) to X(U,V) and Y(U,V), has been
  changed.  Previously surfaces of comparable order to the original
  surfaces were fit to a grid of points, i.e. (U(X,Y), V(X,Y), X) and
  (U(X,Y), V(X,Y), Y), with the same surface fitting routines used in
  <B>fitcoords</B> to obtain the input user coordinate surfaces.  This
  method of inversion worked well in all cases in which reasonable
  distortions and dispersions were used.  It was selected because it was
  relatively fast.  However, it cannot be proved to work in all cases; in
  one instance in which an invalid surface was used the inversion was
  actually much poorer than expected.  Therefore a more direct iterative
  inversion algorithm is now used.  This is guaranteed to give the
  correct inversion to within a set error (0.05 of a pixel in X and Y).
  It is slightly slower than the previous algorithm but it is still not
  as major a factor as the image interpolation itself.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'NOTES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  fitcoords
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMINGS' 'NOTES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>