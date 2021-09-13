.. _geotran:

geotran — Transform 1-D or 2-D images using various mapping transforms
======================================================================

**Package: immatch**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  geotran -- geometrically transform a list of images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  geotran input output database transforms
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be transformed.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images. If the output image name is the same as the input
  image name the input image is overwritten. The output image may be a section
  of an existing image. The number of output images must equal the number
  of input images.
  </DD>
  </DL>
  <DL>
  <DT><B>database</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>The name of the text file containing the coordinate transformation (generally
  the database file produced by GEOMAP).
  If database is the null string then GEOTRAN will perform a linear
  transformation based the values of xin, yin, xout, yout, xshift, yshift,
  xmag, ymag, xrotation and yrotation. If all these parameters have their
  defaults values the transformation is a null transformation. If the geometric
  transformation is linear xin, yin, xout, yout, xshift, yshift, xmag, ymag,
  xrotation and yrotation can be used to override the values in the database
  file.
  </DD>
  </DL>
  <DL>
  <DT><B>transforms</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transforms' Line='transforms'>
  <DD>The list of record name(s) in the file <I>database</I> containing the
  desired transformations.
  This record name is usually the name of the text file input to geomap
  listing the reference and input coordinates of the control points.
  The number of records must be 1 or equal to the number of input images.
  The record names may be listed in a text file 1 record per line.
  The transforms parameter is only
  requested if database is not equal to the null string.
  </DD>
  </DL>
  <DL>
  <DT><B>geometry = "<TT>geometric</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='geometry' Line='geometry = "geometric"'>
  <DD>The type of geometric transformation. The geometry parameter is
  only requested if database is not equal to the null string. The options are:
  <DL>
  <DT><B>linear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Perform only the linear part of the geometric transformation.
  </DD>
  </DL>
  <DL>
  <DT><B>geometric</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='geometric' Line='geometric'>
  <DD>Compute both the linear and distortion portions of the geometric correction.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmin' Line='xmin = INDEF, xmax = INDEF, ymin = INDEF, ymax = INDEF'>
  <DD>The minimum and maximum x and y reference values of the output image.
  If a database file has been defined xmin, xmax, ymin and ymax
  efault to the minimum and maximum values set by
  GEOMAP and may be less than but may not exceed those values.
  </DD>
  </DL>
  <DL>
  <DT><B>xscale = 1.0, yscale = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xscale' Line='xscale = 1.0, yscale = 1.0'>
  <DD>The output picture x and y scales in units of
  x and y reference units per output pixel,
  e.g  arcsec / pixel or Angstroms / pixel if the reference coordinates
  are arcsec or Angstroms. If the reference coordinates are in pixels
  then xscale and yscale should be 1.0 to preserve the scale of the reference
  image.
  If xscale and yscale are undefined (INDEF), xscale and yscale default to the
  range of the reference coordinates over the range in pixels.
  Xscale and yscale override the values of ncols and nlines.
  </DD>
  </DL>
  <DL>
  <DT><B>ncols = INDEF, nlines = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols = INDEF, nlines = INDEF'>
  <DD>The number of columns and lines in the output image. Ncols and nlines default
  to the size of the input image. If xscale or yscale are defined ncols or nlines
  are overridden.
  </DD>
  </DL>
  <DL>
  <DT><B>xsample = 1.0, ysample = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xsample' Line='xsample = 1.0, ysample = 1.0'>
  <DD>The coordinate surface subsampling factor. The coordinate surfaces are
  evaluated at every xsample-th pixel in x and every ysample-th pixel in y.
  Transformed coordinates  at intermediate pixel values are determined by
  bilinear interpolation in the coordinate surfaces. If the coordinate
  surface is of high order setting these numbers to some reasonably high
  value is strongly recommended.
  </DD>
  </DL>
  <DL>
  <DT><B>interpolant = "<TT>linear</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interpolant' Line='interpolant = "linear"'>
  <DD>The interpolant used for rebinning the image.
  The choices are the following.
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Nearest neighbor.
  </DD>
  </DL>
  <DL>
  <DT><B>linear</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='linear' Line='linear'>
  <DD>Bilinear interpolation in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>poly3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly3' Line='poly3'>
  <DD>Third order polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>poly5</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='poly5' Line='poly5'>
  <DD>Fifth order polynomial in x and y.
  </DD>
  </DL>
  <DL>
  <DT><B>spline3</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='spline3' Line='spline3'>
  <DD>Bicubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B>sinc</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sinc' Line='sinc'>
  <DD>2D sinc interpolation. Users can specify the sinc interpolant width by
  appending a width value to the interpolant string, e.g. sinc51 specifies
  a 51 by 51 pixel wide sinc interpolant. The sinc width will be rounded up to
  the nearest odd number.  The default sinc width is 31 by 31.
  </DD>
  </DL>
  <DL>
  <DT><B>lsinc</B></DT>
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
  <DT><B>drizzle</B></DT>
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
  <DT><B>boundary = "<TT>nearest</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The choices are:
  <DL>
  <DT><B>nearest</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a user supplied constant value.
  </DD>
  </DL>
  <DL>
  <DT><B>reflect</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Generate a value by reflecting about the boundary of the image.
  </DD>
  </DL>
  <DL>
  <DT><B>wrap</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Generate a value by wrapping around to the opposite side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.0'>
  <DD>The value of the constant for boundary extension.
  </DD>
  </DL>
  <DL>
  <DT><B>fluxconserve = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fluxconserve' Line='fluxconserve = yes'>
  <DD>Preserve the total image flux. The output pixel values are multiplied by
  the Jacobian of the coordinate transformation.
  </DD>
  </DL>
  <DL>
  <DT><B>xin = INDEF, yin = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xin' Line='xin = INDEF, yin = INDEF'>
  <DD>The x and y coordinates in pixel units in the input image which will map to
  xout, yout in the output image. If the database file is undefined these
  numbers default to the center of the input image. 
  </DD>
  </DL>
  <DL>
  <DT><B>xout = INDEF, yout = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xout' Line='xout = INDEF, yout = INDEF'>
  <DD>The x and y reference coordinates in the output image which correspond
  to xin, yin in the input image. If the database file is undefined, xout and
  yout default to the center of the output image reference coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>xshift = INDEF, yshift = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xshift' Line='xshift = INDEF, yshift = INDEF'>
  <DD>The shift of the input origin in pixels. If the database file is undefined
  then xshift and yshift determine the shift of xin, yin.
  </DD>
  </DL>
  <DL>
  <DT><B>xmag = INDEF, ymag = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag = INDEF, ymag = INDEF'>
  <DD>The scale factors of the coordinate transformation in units of input pixels
  per reference coordinate unit. If database is undefined xmag and ymag
  default to 1.0; otherwise xmag and ymag default to the values found
  by GEOMAP. If the database file is not null then xmag and ymag override
  the values found by GEOMAP.
  </DD>
  </DL>
  <DL>
  <DT><B>xrotation = INDEF, yrotation = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xrotation' Line='xrotation = INDEF, yrotation = INDEF'>
  <DD>The rotation angles in degrees of the coordinate transformation.
  Positive angles are measured counter-clockwise with respect to the x axis.
  If database
  is undefined then xrotation and yrotation default to 0.0; otherwise
  xrotation and yrotation default to the values found by GEOMAP.
  If database is not NULL then xrotation and yrotation override the values
  found by GEOMAP.
  </DD>
  </DL>
  <DL>
  <DT><B>nxblock = 512, nyblock = 512</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxblock' Line='nxblock = 512, nyblock = 512'>
  <DD>If the size of the output image is less than nxblock by nyblock then
  the entire image is transformed at once. Otherwise the output image
  is computed in blocks of nxblock by nxblock pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about the progress of the task ?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  GEOTRAN corrects an image for geometric distortion using the coordinate
  transformation determined by GEOMAP. The transformation is stored as the
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
  and may not exceed those values.
  The scale and size of the output picture is determined as follows.
  <P>
  <PRE>
  	ncols = ncols (inimage)
  	if (xscale == INDEF)
  	    xscale = (xmax - xmin ) / (ncols - 1)
  	else
  	    ncols = (xmax - xmin) / xscale + 1
  <P>
  	nlines = nlines (inimage)
  	if (yscale == INDEF)
  	    yscale = (ymax - ymin ) / (nlines - 1)
  	else
  	    nlines = (ymax - ymin) / yscale + 1
  </PRE>
  <P>
  The output image gray levels are determined by interpolating in the input
  image at the positions of the transformed output pixels. If the
  <I>fluxconserve</I> switch is set the output pixel values are multiplied by
  the Jacobian of the transformation.
  GEOTRAN uses the routines in the 2-D interpolation package.
  <P>
  The linear portion of the transformation may be altered after the fact
  by setting some or all of the parameters <I>xin</I>, <I>yin</I>, <I>xout</I>,
  <I>yout</I>, <I>xshift</I>, <I>yshift</I>, <I>xmag</I>, <I>ymag</I>, <I>xrotation</I>,
  <I>yrotation</I>.
  Xin, yin, xshift, yshift, xout and yout can be used to redefine the shift.
  Xmag, and ymag can be used to reset the x and y scale of the transformation.
  Xrotation and yrotation can be used to reset the orientation of the
  transformation.
  <P>
  The output image is computed in <I>nxblock</I> by <I>nyblock</I> pixel sections.
  If possible users should set these numbers to values larger than the dimensions
  of the output image to minimize the number of disk reads and writes required
  to compute the output image.  If this is not feasible and the image rotation is
  small, users should set nxblock to be greater than the number of columns in
  the output image, and nyblock to be as large as machine memory will permit.
  <P>
  If the CL environment variable <I>nomwcs</I> is "<TT>no</TT>" then the world
  coordinate system of the input image will be modified in the output image
  to reflect the effects of the <I>linear</I> portion of the geometric
  transformation operation.
  Support does not yet exist in the IRAF world coordinate system interface
  for the higher order distortion corrections that GEOTRAN is capable of
  performing.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Timings</H3>
  <! BeginSection: 'TIMINGS'>
  <UL>
  It requires approximately 70 and 290 cpu seconds to correct a 512 by 512
  square image for geometric distortion using a low order coordinate surface
  and bilinear and biquintic interpolation respectively (Vax 11/750 fpa).
  <P>
  </UL>
  <! EndSection:   'TIMINGS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Register two images by transforming the coordinate system of the input
  image to the coordinate system of the reference image. The size of the
  reference image is 512 by 512.  The output image scale will be 1.0 and
  its size will be determined by the xmin, xmax, ymin, ymax parameters set
  in the task GEOMAP. The file "<TT>database</TT>" containing the record "<TT>m51.coo</TT>"
  was produced by GEOMAP.
  <P>
  <PRE>
     cl&gt; geomap m51.coo database 1.0 512.0 1.0 512.0
     cl&gt; geotran m51 m51.tran database m51.coo
  </PRE>
  <P>
  2. Repeat the above command but set the output image scale to 2.0 reference
  images pixels per output image pixel.
  <P>
  <PRE>
     cl&gt; geomap m51.coo database 1.0 512.0 1.0 512.0
     cl&gt; geotran m51 m51.tran database m51.coo xscale=2.0 yscale=2.0
  </PRE>
  <P>
  3. Repeat the previous command using an output scale of
  2 reference units per pixel and bicubic spline interpolation with no
  flux correction. 
  <P>
  <PRE>
     cl&gt; geomap m51.coo database 1.0 512.0 1.0 512.0
     cl&gt; geotran m51 m51.tran database m51.coo xscale=2. yscale=2. \<BR>
     &gt;&gt;&gt; inter=spline3 flux-
  </PRE>
  <P>
  4. Register a list of 512 by 512 pixel square images using the set of
  transforms computed by GEOMAP. The input images, output images, and coordinate
  lists / transforms are listed in the files inlist, outlist and reclist
  respectively.
  <P>
  <PRE>
     cl&gt; geomap @reclist database 1. 512. 1. 512.
     cl&gt; geotran @inlist @outlist database @reclist
  </PRE>
  <P>
  5. Mosaic 3 512 square images into a larger 512 by 1536 square images after
  applying a shift to each input image.
  <P>
  <PRE>
      cl&gt; geotran image1 outimage[1:512,1:512] "" ncols=512 nlines=1536 \<BR>
  	xshift=5.0 yshift=5.0
      cl&gt; geotran image2 outimage[1:512,513:1024] "" xshift=10.0 yshift=10.0
      cl&gt; geotran image3 outimage[1:512,1025:1536] "" xshift=15.0 yshift=15.0
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Support does not yet exist in the IRAF world coordinate system interface
  for the higher order distortion corrections that GEOTRAN is capable of
  performing.
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imshift, magnify, rotate, imlintran, geomap, geoxytran, gregister
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'TIMINGS' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
