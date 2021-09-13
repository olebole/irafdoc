.. _mosproc:

mosproc — Prepare images for quick look mosaicing
=================================================

**Package: irred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mosproc -- Prepare images for quick look mosaicing
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mosproc input output nxsub nysub
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images to be mosaiced. The images are assumed
  to be ordered either by row, column, or in a raster pattern. If
  the image list is not in order then the iraf <B>files</B> task plus
  the <B>editor</B> must be used to construct an image list. The images
  in the input list are assumed to all be the same size.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The name of the output mosaiced image.
  </DD>
  </DL>
  <DL>
  <DT><B>nxsub</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nxsub' Line='nxsub'>
  <DD>The number of subrasters along a row of the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>nysub</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nysub' Line='nysub'>
  <DD>The number of subrasters along a column of the output image.
  </DD>
  </DL>
  <DL>
  <DT><B>skysubtract = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='skysubtract' Line='skysubtract = yes'>
  <DD>Subtract a sky image from all the input images. The sky image
  to be subtracted is either <I>sky</I> or a sky image computed
  by median filtering selected input images after weighting the images
  by the exposure time..
  </DD>
  </DL>
  <DL>
  <DT><B>sky = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sky' Line='sky = ""'>
  <DD>The name of the sky image.
  </DD>
  </DL>
  <DL>
  <DT><B>exclude = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exclude' Line='exclude = ""'>
  <DD>The input images to be excluded from the computation of the sky image.
  For example if <I>exclude</I>="<TT>1,3-5</TT>" then input images 1, 3, 4, 5 are
  not used for computing the sky frame.
  </DD>
  </DL>
  <DL>
  <DT><B>expname = "<TT>exptime</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expname' Line='expname = "exptime"'>
  <DD>The image header exposure time keyword. If the sky frame is computed
  internally by median filtering the input images, the individual images
  are weighted by the exposure time defined by the exposure time
  keyword <I>expname</I>. Weights of 1 are assigned when no exposure time
  is given.
  </DD>
  </DL>
  <DL>
  <DT><B>flatten = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flatten' Line='flatten = yes'>
  <DD>Divide all the images by a flat field image. Flat fielding is done
  after sky subtraction. If the name of a flat field image <I>flat</I>
  is supplied that image is divided directly into all the input images.
  Otherwise the skyframe computed above is normalized by the mode of the
  pixels and divided into all the input images.
  </DD>
  </DL>
  <DL>
  <DT><B>flat = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flat' Line='flat = ""'>
  <DD>The name of the flat field image.
  </DD>
  </DL>
  <DL>
  <DT><B>transpose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transpose' Line='transpose = no'>
  <DD>Transpose the input images before inserting them into the mosaic.
  </DD>
  </DL>
  <DL>
  <DT><B>trim_section = "<TT>[*,*]</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trim_section' Line='trim_section = "[*,*]"'>
  <DD>The section of the input images to be mosaiced into the output
  image. Section can be used to flip and/or trim the individual
  subrasters before adding them to the mosaic. For example if we
  want to flip each subraster around the y axis before adding it
  to the mosaic, then <I>trim_section</I> = "<TT>[*,-*]</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>corner = "<TT>lr</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='corner' Line='corner = "lr"'>
  <DD>The starting position in the output image. The four options are "<TT>ll</TT>" for
  lower left corner, "<TT>lr</TT>" for lower right corner, "<TT>ul</TT>" for upper left
  corner and "<TT>ur</TT>" for upper right corner.
  </DD>
  </DL>
  <DL>
  <DT><B>direction = "<TT>row</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='direction' Line='direction = "row"'>
  <DD>Add input images to the output image in row or column order. The options
  are "<TT>row</TT>" for row order and "<TT>column</TT>" for column order. The direction
  specified must agree with the order of the input list.
  </DD>
  </DL>
  <DL>
  <DT><B>raster = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='raster' Line='raster = no'>
  <DD>Add the columns or rows to the output image in a raster pattern or return
  to the start of a column or a row.
  </DD>
  </DL>
  <DL>
  <DT><B>median_section = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='median_section' Line='median_section = ""'>
  <DD>Compute the median of each input image inserted into the mosaic using the
  specified section.
  </DD>
  </DL>
  <DL>
  <DT><B>subtract = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subtract' Line='subtract = no'>
  <DD>Subtract the computed median from each input image before inserting it
  into the mosaic.
  </DD>
  </DL>
  <DL>
  <DT><B>oval = -1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='oval' Line='oval = -1.0'>
  <DD>The value of border pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>delete = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='delete' Line='delete = yes'>
  <DD>Delete sky subtracted, flat fielded and transposed images upon exit from
  the script.
  </DD>
  </DL>
  <DL>
  <DT><B>logfile = STDOUT</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = STDOUT'>
  <DD>The name of the log file.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  MOSPROC takes the list of input images <I>input</I> of identical dimensions and
  inserts them into a single output image <I>output</I>. Before mosaicing the user
  can optionally sky subtract, flat field or transpose the input images.
  If <I>skysubtract</I> = yes, a single sky
  image is subtracted from all the input images. The sky image
  may be the externally derived image <I>sky</I> or calculated internally 
  by computing the exposure time weighted median of the input images, minus
  those input images specifically excluded by the <I>exclude</I> parameter.
  If <I>flatten</I> = yes, the input images are flat fielded using either
  the externally defined flat field image <I>flat</I> or the internally
  derived sky image normalized by its mode.
  If <I>transpose</I> is enabled all the input images are optionally transposed
  before mosaicing.
  <P>
  MOSPROC takes the list of processed images and inserts them into the 
  output image in positions determined by their order in the input list,
  <I>nxsub</I>, <I>nysub</I> and the parameters  <I>corner</I>, <I>direction</I>
  and <I>raster</I>. 
  The orientation and size of each individual subraster in the output image
  may be altered by setting the parameter <I>trim_section</I>. The size
  of the output image is determined by nxsub and nysub and the size of
  the individual input images. A one column wide border is drawn between
  each of the output image subrasters with a pixel value of <I>oval</I>.
  The user may optionally  compute and subtract the median from each input
  image before inserting it into the mosaic.
  <P>
  MOSPROC produces an output mosaiced image <I>output</I> and an accompanying
  database file <I>dboutput</I>. These two files plus an interactively
  generated coordinate list comprise the necessary input for the IRALIGN,
  IRMATCH1D and IRMATCH2D tasks.
  The temporary images generated (sky substracted, flat fielded, and
  transposed)
  can be deleted automatically if <B>delete=yes</B>, before the task completes.
  Otherwise they will be left in the same directory of the input images.
  The temporary sky and flat field images if created are not deleted.
  <P>
  The computation of the sky frame is done with IMAGES.IMCOMBINE and the
  subsequent sky subraction with IMAGES.IMARITH. The computation of
  the flat field is done with PROTO.BSCALE and the flat field division
  with FLATTEN. The task IMAGES.TRANSPOSE transpose the input.
  The mosaicing itself is done with PROTO.IRMOSAIC.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Mosaic a list of 64 infrared images onto an 8 by 8 grid after sky 
     subtraction and flat fielding. Use an externally derived sky and
     flat field image
   
      ir&gt; mosproc @imlist mosaic 8 8 skysub+ sky=skyimage flatten+ \<BR>
      &gt;&gt;&gt;  flat=flatfield
  <P>
  2. Mosaic a list of 64 infrared images onto an 8 by 8 grid after sky 
     subtraction and flat fielding. Derive the sky and flat field frames
     from the data excluding image number 5
   
      ir&gt; mosproc @imlist mosaic 8 8 skysub+ exclude="<TT>5</TT>" flatten+ 
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
  images.imcombine, images.imarith, proto.bscale, images.imtrans, proto.irmosaic
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
