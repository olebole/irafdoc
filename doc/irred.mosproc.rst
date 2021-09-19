.. _mosproc:

mosproc: Prepare images for quick look mosaicing
================================================

**Package: irred**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  mosproc -- Prepare images for quick look mosaicing
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mosproc input output nxsub nysub
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The list of input images to be mosaiced. The images are assumed
  to be ordered either by row, column, or in a raster pattern. If
  the image list is not in order then the iraf <b>files</b> task plus
  the <b>editor</b> must be used to construct an image list. The images
  in the input list are assumed to all be the same size.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>The name of the output mosaiced image.
  </dd>
  </dl>
  <dl>
  <dt><b>nxsub</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nxsub' Line='nxsub' -->
  <dd>The number of subrasters along a row of the output image.
  </dd>
  </dl>
  <dl>
  <dt><b>nysub</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nysub' Line='nysub' -->
  <dd>The number of subrasters along a column of the output image.
  </dd>
  </dl>
  <dl>
  <dt><b>skysubtract = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='skysubtract' Line='skysubtract = yes' -->
  <dd>Subtract a sky image from all the input images. The sky image
  to be subtracted is either <i>sky</i> or a sky image computed
  by median filtering selected input images after weighting the images
  by the exposure time..
  </dd>
  </dl>
  <dl>
  <dt><b>sky = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='sky' Line='sky = ""' -->
  <dd>The name of the sky image.
  </dd>
  </dl>
  <dl>
  <dt><b>exclude = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='exclude' Line='exclude = ""' -->
  <dd>The input images to be excluded from the computation of the sky image.
  For example if <i>exclude</i>=<tt>"1,3-5"</tt> then input images 1, 3, 4, 5 are
  not used for computing the sky frame.
  </dd>
  </dl>
  <dl>
  <dt><b>expname = <tt>"exptime"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='expname' Line='expname = "exptime"' -->
  <dd>The image header exposure time keyword. If the sky frame is computed
  internally by median filtering the input images, the individual images
  are weighted by the exposure time defined by the exposure time
  keyword <i>expname</i>. Weights of 1 are assigned when no exposure time
  is given.
  </dd>
  </dl>
  <dl>
  <dt><b>flatten = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='flatten' Line='flatten = yes' -->
  <dd>Divide all the images by a flat field image. Flat fielding is done
  after sky subtraction. If the name of a flat field image <i>flat</i>
  is supplied that image is divided directly into all the input images.
  Otherwise the skyframe computed above is normalized by the mode of the
  pixels and divided into all the input images.
  </dd>
  </dl>
  <dl>
  <dt><b>flat = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='flat' Line='flat = ""' -->
  <dd>The name of the flat field image.
  </dd>
  </dl>
  <dl>
  <dt><b>transpose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='transpose' Line='transpose = no' -->
  <dd>Transpose the input images before inserting them into the mosaic.
  </dd>
  </dl>
  <dl>
  <dt><b>trim_section = <tt>"[*,*]"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='trim_section' Line='trim_section = "[*,*]"' -->
  <dd>The section of the input images to be mosaiced into the output
  image. Section can be used to flip and/or trim the individual
  subrasters before adding them to the mosaic. For example if we
  want to flip each subraster around the y axis before adding it
  to the mosaic, then <i>trim_section</i> = <tt>"[*,-*]"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>corner = <tt>"lr"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='corner' Line='corner = "lr"' -->
  <dd>The starting position in the output image. The four options are <tt>"ll"</tt> for
  lower left corner, <tt>"lr"</tt> for lower right corner, <tt>"ul"</tt> for upper left
  corner and <tt>"ur"</tt> for upper right corner.
  </dd>
  </dl>
  <dl>
  <dt><b>direction = <tt>"row"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='direction' Line='direction = "row"' -->
  <dd>Add input images to the output image in row or column order. The options
  are <tt>"row"</tt> for row order and <tt>"column"</tt> for column order. The direction
  specified must agree with the order of the input list.
  </dd>
  </dl>
  <dl>
  <dt><b>raster = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='raster' Line='raster = no' -->
  <dd>Add the columns or rows to the output image in a raster pattern or return
  to the start of a column or a row.
  </dd>
  </dl>
  <dl>
  <dt><b>median_section = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='median_section' Line='median_section = ""' -->
  <dd>Compute the median of each input image inserted into the mosaic using the
  specified section.
  </dd>
  </dl>
  <dl>
  <dt><b>subtract = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='subtract' Line='subtract = no' -->
  <dd>Subtract the computed median from each input image before inserting it
  into the mosaic.
  </dd>
  </dl>
  <dl>
  <dt><b>oval = -1.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='oval' Line='oval = -1.0' -->
  <dd>The value of border pixels.
  </dd>
  </dl>
  <dl>
  <dt><b>delete = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='delete' Line='delete = yes' -->
  <dd>Delete sky subtracted, flat fielded and transposed images upon exit from
  the script.
  </dd>
  </dl>
  <dl>
  <dt><b>logfile = STDOUT</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = STDOUT' -->
  <dd>The name of the log file.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  MOSPROC takes the list of input images <i>input</i> of identical dimensions and
  inserts them into a single output image <i>output</i>. Before mosaicing the user
  can optionally sky subtract, flat field or transpose the input images.
  If <i>skysubtract</i> = yes, a single sky
  image is subtracted from all the input images. The sky image
  may be the externally derived image <i>sky</i> or calculated internally 
  by computing the exposure time weighted median of the input images, minus
  those input images specifically excluded by the <i>exclude</i> parameter.
  If <i>flatten</i> = yes, the input images are flat fielded using either
  the externally defined flat field image <i>flat</i> or the internally
  derived sky image normalized by its mode.
  If <i>transpose</i> is enabled all the input images are optionally transposed
  before mosaicing.
  </p>
  <p>
  MOSPROC takes the list of processed images and inserts them into the 
  output image in positions determined by their order in the input list,
  <i>nxsub</i>, <i>nysub</i> and the parameters  <i>corner</i>, <i>direction</i>
  and <i>raster</i>. 
  The orientation and size of each individual subraster in the output image
  may be altered by setting the parameter <i>trim_section</i>. The size
  of the output image is determined by nxsub and nysub and the size of
  the individual input images. A one column wide border is drawn between
  each of the output image subrasters with a pixel value of <i>oval</i>.
  The user may optionally  compute and subtract the median from each input
  image before inserting it into the mosaic.
  </p>
  <p>
  MOSPROC produces an output mosaiced image <i>output</i> and an accompanying
  database file <i>dboutput</i>. These two files plus an interactively
  generated coordinate list comprise the necessary input for the IRALIGN,
  IRMATCH1D and IRMATCH2D tasks.
  The temporary images generated (sky substracted, flat fielded, and
  transposed)
  can be deleted automatically if <b>delete=yes</b>, before the task completes.
  Otherwise they will be left in the same directory of the input images.
  The temporary sky and flat field images if created are not deleted.
  </p>
  <p>
  The computation of the sky frame is done with IMAGES.IMCOMBINE and the
  subsequent sky subraction with IMAGES.IMARITH. The computation of
  the flat field is done with PROTO.BSCALE and the flat field division
  with FLATTEN. The task IMAGES.TRANSPOSE transpose the input.
  The mosaicing itself is done with PROTO.IRMOSAIC.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Mosaic a list of 64 infrared images onto an 8 by 8 grid after sky 
     subtraction and flat fielding. Use an externally derived sky and
     flat field image
   
      ir&gt; mosproc @imlist mosaic 8 8 skysub+ sky=skyimage flatten+ \<br>
      &gt;&gt;&gt;  flat=flatfield
  </p>
  <p>
  2. Mosaic a list of 64 infrared images onto an 8 by 8 grid after sky 
     subtraction and flat fielding. Derive the sky and flat field frames
     from the data excluding image number 5
   
      ir&gt; mosproc @imlist mosaic 8 8 skysub+ exclude=<tt>"5"</tt> flatten+ 
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  images.imcombine, images.imarith, proto.bscale, images.imtrans, proto.irmosaic
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
