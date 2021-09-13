.. _i2sun:

i2sun — Convert IRAF images to Sun rasterfiles
==============================================

**Package: vol**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  i2sun -- convert IRAF images to Sun rasterfiles
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  i2sun input output z1 z2
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input image template, @file, n-dimensional image, or combination.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Root template for output images, e.g. "<TT>home$ras/frame.%d</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>clutfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clutfile' Line='clutfile'>
  <DD>Previously saved Sun rasterfile (e.g. output from IMTOOL), containing the
  color/greyscale lookup table information to be passed along to each output
  frame.  Standard ones can be saved and used with any number of images (e.g.
  "<TT>pseudo.ras</TT>").
  </DD>
  </DL>
  <DL>
  <DT><B>z1 = INDEF, z2 = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='z1' Line='z1 = INDEF, z2 = INDEF'>
  <DD>Minimum and maximum pixel/voxel intensities to scale to full output
  color/greyscale range.  Both are required parameters, and will apply to all
  images in the sequence.
  </DD>
  </DL>
  <DL>
  <DT><B>ztrans = "<TT>linear</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ztrans' Line='ztrans = "linear"'>
  <DD>Intensity transformation on input data (linear|log|none|user).
  If "<TT>user</TT>", you must also specify <I>ulutfile</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>ulutfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ulutfile' Line='ulutfile'>
  <DD>Name of text file containing the look up table when <I>ztrans</I> = user.
  The table should contain two columns per line; column 1 contains the
  intensity, column 2 the desired greyscale output.
  </DD>
  </DL>
  <DL>
  <DT><B>xsize = INDEF, ysize = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xsize' Line='xsize = INDEF, ysize = INDEF'>
  <DD>If specified, these will be the dimensions of all output Sun rasterfiles
  in pixels.  The default will be the same size as the input images (which
  could vary, though this would create a jittery movie).
  </DD>
  </DL>
  <DL>
  <DT><B>xmag = 1.0, ymag = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xmag' Line='xmag = 1.0, ymag = 1.0'>
  <DD>Another way to specify output rasterfile dimensions.  These are the 
  magnification factors to apply to the input image dimensions.
  </DD>
  </DL>
  <DL>
  <DT><B>order = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>Order of the interpolator to be used for spatially interpolating the image.
  The current choices are 0 for pixel replication, and 1 for bilinear
  interpolation.
  </DD>
  </DL>
  <DL>
  <DT><B>sliceaxis = 3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sliceaxis' Line='sliceaxis = 3'>
  <DD>Image axis from which to cut multiple slices when input image dimension is
  greater than 2.  Only x-y sections are allowed, so <I>sliceaxis</I> must
  be 3 or greater.
  </DD>
  </DL>
  <DL>
  <DT><B>swap = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='swap' Line='swap = no'>
  <DD>Swap rasterfile bytes on output?  Used when rasterfiles are being written
  to a computer with opposite byte-swapping from that of the home computer
  (e.g. between VAX and Sun).
  </DD>
  </DL>
  <P>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  Given a series of IRAF images, an intensity transformation, and a file
  containing color/greyscale lookup table information, produces one 2d image
  in Sun rasterfile format for each 2D IRAF image.  This is a temporary task
  usually used as a step in creating filmloops for playback by a Sun Movie
  program.
  <P>
  The input images may be specified as an image template ("<TT>zoom*.imh</TT>"),
  an "<TT>@</TT>" file ("<TT>@movie.list</TT>"), or as an n-dimensional image from which to
  create multiple 2d rasterfiles.  If any images in a list are nD images,
  all 2d sections from the specified <I>sliceaxis</I> will be written out
  (default = band or z axis).  At present, only x-y sections may be made,
  i.e. the slice axis must be axis 3 or higher.
  <P>
  The minimum and maximum pixel/voxel intensities, z1 and z2, must be specified
  as it would be not only inefficient to calculate the full zrange of
  each image in a sequence, but would also make very jumpy movies.
  Between input intensities z1 and z2, the pixel intensities may be transformed
  according to the <I>ztrans</I> parameter: "<TT>linear</TT>", "<TT>log10</TT>", "<TT>none</TT>",
  or "<TT>user</TT>".
  <P>
  When <I>ztrans</I> = "<TT>user</TT>", a look up table of intensity values and their
  corresponding greyscale levels is read from the file specified by the
  <I>ulutfile</I> parameter.  From this information, a piecewise linear
  look up table containing 4096 discrete values is composed.  The text
  format table contains two columns per line; column 1 contains the
  intensity, column 2 the desired greyscale output.  The greyscale values
  specified by the user must match those available on the output device.
  Task <I>showcap</I> can be used to determine the range of acceptable
  greyscale levels.  
  <P>
  A color table file (<I>clutfile</I>) may be produced on a Sun workstation from
  IMTOOL (see IMTOOL manual page, R_RASTERFILE parameter and Imcopy function).
  This file may be specified to I2SUN as the <I>clutfile</I> parameter.
  Likewise, any rasterfiles previously created with
  I2SUN may be used as input clutfiles.
  <P>
  The output rasterfile dimensions may be larger or smaller than the input 
  images (see parameters <I>xsize</I> and <I>ysize</I>, or <I>xmag</I> and
  <I>ymag</I>).  The parameter <I>order</I> controls the mode of interpolation;
  0=pixel replication, 1=bilinear.
  <P>
  If the output rasterfiles are being sent to a computer with opposite
  byte-swapping characteristics, set <I>swap</I> = yes (e.g., when running
  I2SUN on a VAX, with output to a Sun).
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  1.  Produce a series of Sun rasterfiles in tmp$mydir/movie/,
      using a pseudocolor color table file saved earlier, with
      input greylevels scaled between 10 and 100.
  <P>
      cl&gt; i2sun nzoom*.imh tmp$mydir/movie/frame.%d \<BR>
  	home$colors/pseudo.ras 10 100
  <P>
  2.  Make a movie through the z, or band, axis of a datacube.
  <P>
      cl&gt; i2sun cube tmp$cubemovie/frame.%d 1 256 
  <P>
  3.  Make a movie through the 4th, or hyper-axis of a datacube,
      holding image band 10 constant.
  <P>
      cl&gt; i2sun hypercube[*,*,10,*] tmp$movie/frame.%d 1 256 \<BR>
  	sliceaxis=4
  <P>
  4.  Run I2SUN on a VAX, with output to a Sun.
  <P>
      cl&gt; i2sun @imlist sunnode!home$ras/frame.%d 1 256 swap+
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Timings</H3>
  <! BeginSection: 'TIMINGS'>
  <UL>
  49 seconds (1 sec/frame) to produce 50 100*100 rasterfiles from a
  100*100*50 datacube with no magnification, on a diskless Sun-3/110
  using NFS to Eagle disks on a lightly loaded Sun-3/160 fileserver
  (load factor &lt; 1.5).  
  5 minutes for the same with a magnification factor of 2 in both x and y,
  bilinear interpolation.
  20 minutes for the same with a magnification factor of 5 in both x and y.
  </UL>
  <! EndSection:   'TIMINGS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  display, imtool, volumes.pvol
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIMINGS' 'BUGS' 'SEE ALSO'  >
  
