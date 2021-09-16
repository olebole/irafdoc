.. _quadproc:

quadproc — Process multi-amplifier CCD images (see also ccdproc)
================================================================

**Package: quadred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  quadproc -- Process multi-readout CCD images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  quadproc images
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of input CCD images to process.  The list may include processed
  images and calibration images.
  </DD>
  </DL>
  <DL>
  <DT><B>ccdtype = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = ""'>
  <DD>CCD image type to select from the input image list.  If no type is given
  then all input images will be selected.  The recognized types are described
  in <B>ccdtypes</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>max_cache = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='max_cache' Line='max_cache = 0'>
  <DD>Maximum image caching memory (in Mbytes).  If there is sufficient memory
  the calibration images, such as zero level, dark count, and flat fields,
  will be cached in memory when processing many input images.  This
  reduces the disk I/O and makes the task run a little faster.  If the
  value is zero image caching is not used.
  </DD>
  </DL>
  <DL>
  <DT><B>noproc = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='noproc' Line='noproc = no'>
  <DD>List processing steps only?
  </DD>
  </DL>
  <P>
  <CENTER>PROCESSING SWITCHES
  
  </CENTER><BR>
  <DL>
  <DT><B>fixpix = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fixpix' Line='fixpix = yes'>
  <DD>Fix bad CCD lines and columns by linear interpolation from neighboring
  lines and columns?  If yes then a bad pixel file must be specified.
  </DD>
  </DL>
  <DL>
  <DT><B>overscan = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='overscan' Line='overscan = yes'>
  <DD>Apply overscan or prescan bias correction?  If yes then the overscan
  image section and the readout axis must be specified.
  </DD>
  </DL>
  <DL>
  <DT><B>trim = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trim' Line='trim = yes'>
  <DD>Trim the image of the overscan region and bad edge lines and columns?
  If yes then the trim section must be specified.
  </DD>
  </DL>
  <DL>
  <DT><B>zerocor = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zerocor' Line='zerocor = yes'>
  <DD>Apply zero level correction?  If yes a zero level image must be specified.
  </DD>
  </DL>
  <DL>
  <DT><B>darkcor = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='darkcor' Line='darkcor = yes'>
  <DD>Apply dark count correction?  If yes a dark count image must be specified.
  </DD>
  </DL>
  <DL>
  <DT><B>flatcor = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flatcor' Line='flatcor = yes'>
  <DD>Apply flat field correction?  If yes flat field images must be specified.
  </DD>
  </DL>
  <DL>
  <DT><B>illumcor = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='illumcor' Line='illumcor = no'>
  <DD>Apply iillumination correction?  If yes iillumination images must be specified.
  </DD>
  </DL>
  <DL>
  <DT><B>fringecor = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fringecor' Line='fringecor = no'>
  <DD>Apply fringe correction?  If yes fringe images must be specified.
  </DD>
  </DL>
  <DL>
  <DT><B>readcor = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='readcor' Line='readcor = no'>
  <DD>Convert zero level images to readout correction images?  If yes then
  zero level images are averaged across the readout axis to form one
  dimensional zero level readout correction images.
  </DD>
  </DL>
  <DL>
  <DT><B>scancor = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scancor' Line='scancor = no'>
  <DD>Convert flat field images to scan mode flat field images?  If yes then the
  form of scan mode correction is specified by the parameter <I>scantype</I>.
  </DD>
  </DL>
  <P>
  <CENTER>PROCESSING PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>readaxis = "<TT>line</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='readaxis' Line='readaxis = "line"'>
  <DD>Read out axis specified as "<TT>line</TT>" or "<TT>column</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>fixfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fixfile' Line='fixfile'>
  <DD>File describing the bad lines and columns.  If "<TT>image</TT>" is specified then
  the file is specified in the image header or instrument translation file.
  See Section 2. of Description for further information on bad pixel files.
  </DD>
  </DL>
  <DL>
  <DT><B>biassec</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='biassec' Line='biassec'>
  <DD>Overscan bias strip image section.  If "<TT>image</TT>" is specified then the overscan
  bias section is specified in the image header or instrument translation file.
  See Section 3. of Description for further information on setting this parmeter.
  </DD>
  </DL>
  <DL>
  <DT><B>trimsec</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trimsec' Line='trimsec'>
  <DD>image section for trimming.  If "<TT>image</TT>" is specified then the trim
  image section is specified in the image header or instrument translation file.
  See Section 4. of Description for further information on setting this parmeter.
  </DD>
  </DL>
  <DL>
  <DT><B>zero = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zero' Line='zero = ""'>
  <DD>Zero level calibration image.  The zero level image may be one or two
  dimensional.  The CCD image type and subset are not checked for these
  images and they take precedence over any zero level calibration images
  given in the input list.
  </DD>
  </DL>
  <DL>
  <DT><B>dark = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dark' Line='dark = ""'>
  <DD>Dark count calibration image.  The CCD image type and subset are not checked
  for these images and they take precedence over any dark count calibration
  images given in the input list.
  </DD>
  </DL>
  <DL>
  <DT><B>flat = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flat' Line='flat = ""'>
  <DD>Flat field calibration images.  The flat field images may be one or
  two dimensional.  The CCD image type is not checked for these
  images and they take precedence over any flat field calibration images given
  in the input list.  The flat field image with the same subset as the
  input image being processed is selected.
  </DD>
  </DL>
  <DL>
  <DT><B>illum = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='illum' Line='illum = ""'>
  <DD>Iillumination correction images.  The CCD image type is not checked for these
  images and they take precedence over any iillumination correction images given
  in the input list.  The iillumination image with the same subset as the
  input image being processed is selected.
  </DD>
  </DL>
  <DL>
  <DT><B>fringe = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fringe' Line='fringe = ""'>
  <DD>Fringe correction images.  The CCD image type is not checked for these
  images and they take precedence over any fringe correction images given
  in the input list.  The fringe image with the same subset as the
  input image being processed is selected.
  </DD>
  </DL>
  <DL>
  <DT><B>minreplace = 1.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minreplace' Line='minreplace = 1.'>
  <DD>When processing flat fields, pixel values below this value (after
  all other processing such as overscan, zero, and dark corrections) are
  replaced by this value.  This allows flat fields processed by <B>quadproc</B>
  to be certain to avoid divide by zero problems when applied to object
  images.
  </DD>
  </DL>
  <DL>
  <DT><B>scantype = "<TT>shortscan</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scantype' Line='scantype = "shortscan"'>
  <DD>Type of scan format used in creating the CCD images.  The modes are:
  <DL>
  <DT><B>"<TT>shortscan</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"shortscan"'>
  <DD>The CCD is scanned over a number of lines and then read out as a regular
  two dimensional image.  In this mode unscanned flat fields are numerically
  scanned to form scanned flat fields comparable to the observations.  If
  the flat field calibration images are taken in scanned mode then
  <I>scancor</I> should be no and the processing performed in the same manner
  as in unscanned mode.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>longscan</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"longscan"'>
  <DD>In this mode the CCD is clocked and read out continuously to form a long
  strip.  Flat fields are averaged across the readout axis to
  form a one dimensional flat field readout correction image.  This assumes
  that all recorded image lines are clocked over the entire active area of the
  CCD.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>nscan</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nscan' Line='nscan'>
  <DD>Number of scan readout lines used in short scan mode.  This parameter is used
  when the scan type is "<TT>shortscan</TT>".
  </DD>
  </DL>
  <P>
  <CENTER>OVERSCAN FITTING PARAMETERS
  
  </CENTER><BR>
  <DL>
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Fit the overscan vector interactively?  If yes the overscan vector is fit
  interactively using the <B>icfit</B> package.  If no then the fitting parameters
  given below are used.
  </DD>
  </DL>
  <DL>
  <DT><B>function = "<TT>legendre</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "legendre"'>
  <DD>Overscan fitting function.  The function types are "<TT>legendre</TT>" polynomial,
  "<TT>chebyshev</TT>" polynomial, "<TT>spline1</TT>" linear spline, and "<TT>spline3</TT>" cubic
  spline.
  </DD>
  </DL>
  <DL>
  <DT><B>order = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 1'>
  <DD>Number of polynomial terms or spline pieces in the overscan fit.
  </DD>
  </DL>
  <DL>
  <DT><B>sample = "<TT>*</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample' Line='sample = "*"'>
  <DD>Sample points to use in the overscan fit.  The string "<TT>*</TT>" specified all
  points otherwise an <B>icfit</B> range string is used.
  </DD>
  </DL>
  <DL>
  <DT><B>naverage = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='naverage' Line='naverage = 1'>
  <DD>Number of points to average or median to form fitting points.  Positive
  numbers specify averages and negative numbers specify medians.
  </DD>
  </DL>
  <DL>
  <DT><B>niterate = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niterate' Line='niterate = 1'>
  <DD>Number of rejection iterations to remove deviant points from the overscan fit.
  If 0 then no points are rejected.
  </DD>
  </DL>
  <DL>
  <DT><B>low_reject = 3., high_reject = 3.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 3., high_reject = 3.'>
  <DD>Low and high sigma rejection factors for rejecting deviant points from the
  overscan fit.
  </DD>
  </DL>
  <DL>
  <DT><B>grow = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='grow' Line='grow = 0.'>
  <DD>One dimensional growing radius for rejection of neighbors to deviant points.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Quadproc</B> processes CCD images to remove all "<TT>instrumental signatures</TT>" from
  the data. The operations performed are:
  <DL>
  <DT><B></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=' '>
  <DD><PRE>
  o correct detector defects (bad lines and columns)
  o determine readout bias level using overscan and subtract it
  o trim off the overscan regions and unwanted border pixels
  o subtract zero level bias
  o subtract dark counts
  o correct for pixel-to-pixel sensitivity variations
  o correct for non-uniform iillumination
  o correct for fringing
  </PRE>
  </DD>
  </DL>
  <BR>
  <B>Quadproc</B> is a cl script based on the task <B>ccdproc</B> in the
  <B>ccdred</B> package. It is specifically designed to deal with Arcon data
  obtained in multi-readout mode (see <B>quadformat</B>). A feature of such
  images is that each readout typically has a slightly different, DC bias
  level, gain, and readout noise. As a result both zero frames and uniformly 
  illuminated exposures show a characteristic chequer board pattern, the
  sections of the image read through each amplifier having different levels.
  In addition, there will be a separate overscan strip, used to monitor the zero
  level, for each readout. The location of these overscan strips in the raw
  frame depends on which amplifiers are used. <B>Quadproc</B> splits each 
  multi-readout image into subimages, one for each amplifier, and also calculates
  the biassec and trimsec appropriately for each. It then calls <B>ccdproc</B> to
  perform the first three operations listed above. The sub-images are then glued
  back together. Finaly, <B>ccdproc</B> is called a second time to perform all the
  remaining reduction steps. 
  <P>
  <B>Quadproc</B> MUST be used for the reduction of multi-readout data up to and
  including the trimming step, and it is convenient to use it for the entire
  reduction process. However, once ALL images have been trimmed it is possible
  to finish the reductions using <B>ccdproc</B> if the <B>quad</B> package is not
  available at your home institution. <B>Quadproc</B> recognizes mono-readout
  images and processes them directly using <B>ccdproc</B>. If your images are a
  mixture of multi- and mono- readout use <B>quadproc</B>; if you only have
  mono-readout data use <B>ccdproc</B>.
  <P>
  <B>Quadproc</B> is identical to <B>ccdproc</B> in the way it is used, and has
  exactly the same parameters; as far as possible it also behaves in the same way.
  To run it, all one has to do is set the parameters and then begin processing
  the images.  The task takes care of most of the record keeping and
  automatically does the prerequisite processing of calibration images. For
  ease of reference, the following sections provide a simple outline of how to
  use the task, together with a description of the operations performed. They 
  are taken almost verbatim from the help page for <B>ccdproc</B>. If you are 
  already familiar with that task you should read sections 2., 3. and 4. below,
  which include information on the preparation of the badpixel file, and on how
  to specify <B>biassec</B> and <B>trimsec</B> parameters. See section 12. for a
  description of the differences between the two tasks. For a user's guide and 
  cookbook for the <B>quad</B> package see <B>guide</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>1. parameters</H3>
  <! BeginSection: '1. Parameters'>
  <UL>
  There are many parameters but they may be easily reviewed and modified using
  the task <B>eparam</B>.
  The input CCD images to be processed are given as an image list.
  Previously processed images are ignored and calibration images are
  recognized, provided the CCD image types are in the image header (see
  <B>instruments</B> and <B>ccdtypes</B>).  <B>Quadproc</B> separates multi- and
  mono-readout images in the input list and handles them accordingly.
  Therefore it is permissible to use simple image templates such as "<TT>*.imh</TT>".
  The <I>ccdtype</I> parameter may be used to select only certain types of CCD
  images to process (see <B>ccdtypes</B>).
  <P>
  The processing operations are selected by boolean (yes/no) parameters.
  Because calibration images are recognized and processed appropriately,
  the processing operations for object images should be set. Any combination of
  operations may be specified. Two of the operations, <B>readcor</B> and <B>scancor</B>, are only applicable to zero level and flat field images respectively. These
  are used for certain types of CCDs and modes of operation.
  <P>
  The processing steps selected have related parameters which must be
  set.  These are things like image sections defining the overscan and
  trim regions and calibration images.  There are a number of parameters
  used for fitting the overscan or prescan bias section.  These are
  parameters used by the standard IRAF curve fitting package <B>icfit</B>.
  The parameters are described in more detail in the following sections.
  <P>
  In addition to the task parameters there are package parameters
  which affect <B>quadproc</B>.  These include the instrument and subset
  files, the text and plot log files, the output pixel datatype,
  the verbose parameter for logging to the terminal, and the backup
  prefix.  These are described in <B>quad</B>.
  <P>
  Calibration images are specified by task parameters and/or in the
  input image list.  If more than one calibration image is specified
  then the first one encountered is used. Calibration images specified by
  task parameters take precedence over calibration images in the input list.
  These images also need not have a CCD image type parameter since the task
  parameter identifies the type of calibration image.  This method is
  best if there is only one calibration image for all images
  to be processed, almost always true for zero level and dark
  count images.  If no calibration image is specified by task parameter
  then calibration images in the input image list are identified and
  used.  This requires that the images have CCD image types recognized
  by the package.  This method is useful if one may simply say "<TT>*.imh</TT>"
  as the image list to process all images or if the images are broken
  up into groups, in "<TT>@</TT>" files for example, each with their own calibration
  frames.
  </UL>
  <! EndSection:   '1. Parameters'>
  <H3>2. fixpix</H3>
  <! BeginSection: '2. Fixpix'>
  <UL>
  Regions of bad lines and columns may be replaced by linear
  interpolation from neighboring lines and columns when the parameter
  <I>fixpix</I> is set.  The bad regions are specified in a bad pixel
  file.  The file consists of lines with four fields, the starting and
  ending columns and the starting and ending lines.  Any number of
  regions may be specified. Currently, the coordinates given for the bad regions
  must be those that would be applicable if the CCD was used in SINGLE READOUT
  MODE, even if multi-readout images are being reduced. A task is being written
  to aid in the preparation of an appropriate bad-pixel file given measurements
  made on a raw multi-readout image.
  <P>
  Comment lines beginning with the character <TT>'#'</TT> may be included. If a comment
  line preceding the bad regions contains the word "<TT>untrimmed</TT>" then the
  coordinate system refers to the original format of the images; i.e.  before 
  trimming.  If an image has been trimmed previously then the trim region
  specified in the image header is used to convert the coordinates in the bad
  pixel file to those of the trimmed image.  If the file does not contain the
  word "<TT>untrimmed</TT>" then the coordinate system must match that of the image
  being corrected; i.e. untrimmed coordinates if the image has not been
  trimmed and trimmed coordinates if the image has been trimmed.
  Standard bad pixel files should always be specified in terms of the original
  format.
  <P>
  The bad pixel file may be specified explicitly with the parameter <I>fixfile</I>
  or indirectly if the parameter has the value "<TT>image</TT>".  In the latter case
  the instrument file must contain the name of the file.
  </UL>
  <! EndSection:   '2. Fixpix'>
  <H3>3. overscan</H3>
  <! BeginSection: '3. Overscan'>
  <UL>
  The portion of the image used to determine the readout bias level is specified
  with the parameter <B>biassec</B>. This may be an explicit image section, or it
  may be set to the special value "<TT>image</TT>". In the latter case the value given in
  the image header is used.  The image header value uses the entire overscan 
  strip without allowing any margin between the data section and the bias
  section.  Because Arcon uses a DC-coupled preamplifier the transition
  between data and overscan is very sharp indeed. Nonetheless, we recommend that
  you do skip the first few pixels of the overscan strip. To decide this issue
  for yourself, use implot to plot the average of several lines from a high 
  exposure level image such as a flat field. Expand the transition region 
  between data and overscan and decide how many pixels of the overscan are
  contaminated.
  <P>
  In the case of multi-readout images, the way in which an explicit value for
  <B>biassec</B> must be set, is unfortunately somewhat non-intuitive.  Currently,
  the value recorded in the image header is that which would be appropriate had
  the detector been read out using a single amplifier; an explicit image section
  must be specified in the same way. <B>Quadproc</B> calculates the sections
  to use for the sub-images corresponding to each readout based on such "<TT>single
  readout</TT>" sections. To determine the section you must enter, use <B>imhead</B>
  or <B>hselect</B> to determine the value of <B>biassec</B> stored in the image 
  header. If this is, for instance,  "<TT>[1025:1060,1:1028]</TT>" then setting 
  <B>biassec</B> = "<TT>[1029:1060,1:1028]</TT>" would leave  a margin of 4 pixels
  (1029 - 1025).  Note that if two readouts are used in the horizontal direction 
  (quad or serial-split dual readout) the overscan strip for each amplifier is
  only half as wide as that in single readout mode. Thus in the example a 15
  pixel (36 / 2 - 3) wide strip is used for each readout.
  <P>
  If an overscan or prescan correction is specified (<I>overscan</I>
  parameter) then the specified image section is averaged
  along the readout axis (<I>readaxis</I> parameter) to form a
  correction vector.  A function is fit to this vector and for each readout
  line (image line or column) the function value for that line is
  subtracted from the image line.  The fitting function is generally
  either a constant (polynomial of 1 term) or a high order function
  which fits the large scale shape of the overscan vector.  Bad pixel
  rejection is also used to eliminate cosmic ray events.  The function
  fitting may be done interactively using the standard <B>icfit</B>
  iteractive graphical curve fitting tool.  Regardless of whether the fit
  is done interactively, the overscan vector and the fit may be recorded
  for later review in a metacode plot file named by the parameter
  <I>quad.plotfile</I>.  The mean value of the bias function is also recorded in
  the image header and log file.
  <P>
  The overscan subtraction performed by <B>quadproc</B> corrects the 
  amplifier-to-amplifier differences in the bias level, so that no
  readout structure should be visible in processed zero images. However, you
  will still see the chequer board structure in flatfield and object exposures
  (unless the sky level is zero) because of gain difference between the
  amplifiers.
  </UL>
  <! EndSection:   '3. Overscan'>
  <H3>4. trim</H3>
  <! BeginSection: '4. Trim'>
  <UL>
  When the parameter <I>trim</I> is set the input image will be trimmed to
  the image section given by the parameter <I>trimsec</I>. This may be an explicit
  image section, or it may be set to the special value "<TT>image</TT>". In the latter
  case the value given in the image header is used.  The image header value keeps
  the entire imaging section of the CCD.
  <P>
  In the case of multi-readout images, the way in which an explicit value for
  <B>trimsec</B> must be set, is unfortunately somewhat non-intuitive.  Currently,
  the value recorded in the image header is that which would be appropriate had
  the detector been read out using a single amplifier; an explicit image section
  must be specified in the same way. <B>Quadproc</B> calculates the sections
  to use for the sub-images corresponding to each readout based on such "<TT>single
  readout</TT>" sections. In addition one is currently restricted to trimming exactly
  the same number of columns from each side of the CCD; there is no such 
  restriction on the number of lines which can be trimmed from the top and bottom
  edges of the image. To determine the section you must enter, use <B>imhead</B>
  or <B>hselect</B> to determine the value of <B>trimsec</B> stored in the image
  header. If this is, for instance, "<TT>[1:1024,1:1028]</TT>" then setting
  <B>trimsec</B> = "<TT>[10:1015,20:998]</TT>" would trim 9 columns from the left and right
  edges and 19 and 29 lines from the bottom and top edges respectively. If you
  need to perform an asymmetric trim in the horizontal direction this can be
  done, after processing, by using <B>imcopy</B> to copy the required portion of
  the image.
  <P>
  The trim section used for science images should, of course, be the same as 
  that used for the calibration images.
  </UL>
  <! EndSection:   '4. Trim'>
  <H3>5. zerocor</H3>
  <! BeginSection: '5. Zerocor'>
  <UL>
  After the readout bias is subtracted, as defined by the overscan or prescan
  region, there may still be a zero level bias.  This level may be two
  dimensional or one dimensional (the same for every readout line).  A
  zero level calibration is obtained by taking zero length exposures;
  generally many are taken and combined.  To apply this zero
  level calibration the parameter <I>zerocor</I> is set.  In addition if
  the zero level bias is only readout dependent then the parameter <I>readcor</I>
  is set to reduce two dimensional zero level images to one dimensional
  images.  The zero level images may be specified by the parameter <I>zero</I>
  or given in the input image list (provided the CCD image type is defined).
  <P>
  When the zero level image is needed to correct an input image it is checked
  to see if it has been processed and, if not, it is processed automatically.
  Processing of zero level images consists of bad pixel replacement,
  overscan correction, trimming, and averaging to one dimension if the
  readout correction is specified.
  </UL>
  <! EndSection:   '5. Zerocor'>
  <H3>6. darkcor</H3>
  <! BeginSection: '6. Darkcor'>
  <UL>
  Dark counts are subtracted by scaling a dark count calibration image to
  the same exposure time as the input image and subtracting.  The
  exposure time used is the dark time which may be different than the
  actual integration or exposure time.  A dark count calibration image is
  obtained by taking a very long exposure with the shutter closed; i.e.
  an exposure with no light reaching the detector.  The dark count
  correction is selected with the parameter <I>darkcor</I> and the dark
  count calibration image is specified either with the parameter
  <I>dark</I> or as one of the input images.  The dark count image is
  automatically processed as needed.  Processing of dark count images
  consists of bad pixel replacement, overscan and zero level correction,
  and trimming.
  </UL>
  <! EndSection:   '6. Darkcor'>
  <H3>7. flatcor</H3>
  <! BeginSection: '7. Flatcor'>
  <UL>
  The relative detector pixel response is calibrated by dividing by a
  scaled flat field calibration image.  A flat field image is obtained by
  exposure to a spatially uniform source of light such as an lamp or
  twilight sky.  Flat field images may be corrected for the spectral
  signature in spectroscopic images (see <B>response</B> and
  <B>apnormalize</B>), or for iillumination effects (see <B>mkillumflat</B>
  or <B>mkskyflat</B>).  For more on flat fields and iillumination corrections
  see <B>flatfields</B>.  The flat field response is dependent on the
  wavelength of light so if different filters or spectroscopic wavelength
  coverage are used a flat field calibration for each one is required.
  The different flat fields are  automatically selected by a subset
  parameter (see <B>subsets</B>).
  <P>
  Flat field calibration is selected with the parameter <B>flatcor</B>
  and the flat field images are specified with the parameter <B>flat</B>
  or as part of the input image list.  The appropriate subset is automatically
  selected for each input image processed.  The flat field image is
  automatically processed as needed.  Processing consists of bad pixel
  replacement, overscan subtraction, zero level subtraction, dark count
  subtraction, and trimming.  Also if a scan mode is used and the
  parameter <I>scancor</I> is specified then a scan mode correction is
  applied (see below).  The processing also computes the mean of the
  flat field image which is used later to scale the flat field before
  division into the input image.  For scan mode flat fields the ramp
  part is included in computing the mean which will affect the level
  of images processed with this flat field.  Note that there is no check for
  division by zero in the interest of efficiency.  If division by zero
  does occur a fatal error will occur.  The flat field can be fixed by
  replacing small values using a task such as <B>imreplace</B> or
  during processing using the <I>minreplace</I> parameter.  Note that the
  <I>minreplace</I> parameter only applies to flat fields processed by
  <B>quadproc</B>.
  </UL>
  <! EndSection:   '7. Flatcor'>
  <H3>8. illumcor</H3>
  <! BeginSection: '8. Illumcor'>
  <UL>
  CCD images processed through the flat field calibration may not be
  completely flat (in the absence of objects).  In particular, a blank
  sky image may still show gradients.  This residual nonflatness is called
  the iillumination pattern.  It may be introduced even if the detector is
  uniformly illuminated by the sky because the flat field lamp
  iillumination may be nonuniform.  The iillumination pattern is found from a
  blank sky, or even object image, by heavily smoothing and rejecting
  objects using sigma clipping.  The iillumination calibration image is
  divided into the data being processed to remove the iillumination
  pattern.  The iillumination pattern is a function of the subset so there
  must be an iillumination correction image for each subset to be
  processed.  The tasks <B>mkillumcor</B> and <B>mkskycor</B> are used to
  create the iillumination correction images.  For more on iillumination
  corrections see <B>flatfields</B>.
  <P>
  An alternative to treating the iillumination correction as a separate
  operation is to combine the flat field and iillumination correction
  into a corrected flat field image before processing the object
  images.  This will save some processing time but does require creating
  the flat field first rather than correcting the images at the same
  time or later.  There are two methods, removing the large scale
  shape of the flat field and combining a blank sky image iillumination
  with the flat field.  These methods are discussed further in the
  tasks which create them; <B>mkillumcor</B> and <B>mkskycor</B>.
  </UL>
  <! EndSection:   '8. Illumcor'>
  <H3>9. fringecor</H3>
  <! BeginSection: '9. Fringecor'>
  <UL>
  There may be a fringe pattern in the images due to the night sky lines.
  To remove this fringe pattern a blank sky image is heavily smoothed
  to produce an iillumination image which is then subtracted from the
  original sky image.  The residual fringe pattern is scaled to the
  exposure time of the image to be fringe corrected and then subtracted.
  Because the intensity of the night sky lines varies with time an
  additional scaling factor may be given in the image header.
  The fringe pattern is a function of the subset so there must be
  a fringe correction image for each subset to be processed.
  The task <B>mkfringecor</B> is used to create the fringe correction images.
  </UL>
  <! EndSection:   '9. Fringecor'>
  <H3>10. readcor</H3>
  <! BeginSection: '10. Readcor'>
  <UL>
  If a zero level correction is desired (<I>zerocor</I> parameter)
  and the parameter <I>readcor</I> is yes then a single zero level
  correction vector is applied to each readout line or column.  Use of a
  readout correction rather than a two dimensional zero level image
  depends on the nature of the detector or if the CCD is operated in
  longscan mode (see below).  The readout correction is specified by a
  one dimensional image (<I>zero</I> parameter) and the readout axis
  (<I>readaxis</I> parameter).  If the zero level image is two dimensional
  then it is automatically processed to a one dimensional image by
  averaging across the readout axis.  Note that this modifies the zero
  level calibration image.
  </UL>
  <! EndSection:   '10. Readcor'>
  <H3>11. scancor</H3>
  <! BeginSection: '11. Scancor'>
  <UL>
  CCD detectors may be operated in several modes in astronomical
  applications.  The most common is as a direct imager where each pixel
  integrates one point in the sky or spectrum.  However, the design of most CCD's
  allows the sky to be scanned across the CCD while shifting the
  accumulating signal at the same rate.  <B>Quadproc</B> provides for two
  scanning modes called "<TT>shortscan</TT>" and "<TT>longscan</TT>".  The type of scan
  mode is set with the parameter <I>scanmode</I>.
  <P>
  In "<TT>shortscan</TT>" mode the detector is scanned over a specified number of
  lines (not necessarily at sideral rates).  The lines that scroll off
  the detector during the integration are thrown away.  At the end of the
  integration the detector is read out in the same way as an unscanned
  observation.  The advantage of this mode is that the small scale flat
  field response is averaged in one dimension over the number of lines
  scanned.  A flat field may be observed in the same way in which case
  there is no difference in the processing from unscanned imaging and the
  parameter <I>scancor</I> should be no.  However, one obtains an increase
  in the statistical accuracy of the flat fields if they are not scanned
  during the observation but digitally scanned during the processing.  In
  shortscan mode with <I>scancor</I> set to yes, flat field images are
  digitally scanned, if needed, by the specified number of scan lines
  (<I>nscan</I> parameter).
  <P>
  In "<TT>longscan</TT>" mode the detector is continuously read out to produce
  an arbitrarily long strip.  Provided data which has not passed over
  the entire detector is thrown away, the flat field corrections will
  be one dimensional.  If <I>scancor</I> is specified and the
  scan mode is "<TT>longscan</TT>" then a one dimensional flat field correction
  will be applied.  If the specified flat field (<I>flat</I> parameter)
  is a two dimensional image then when the flat field image is processed
  it will be averaged across the readout axis to form a one dimensional
  correction image.
  </UL>
  <! EndSection:   '11. Scancor'>
  <H3>12. outline of processing steps</H3>
  <! BeginSection: '12. Outline of Processing Steps'>
  <UL>
  <P>
  Because of the special handling required for multi-readout data
  <B>quadproc</B> internally reduces the data in two stages.
  <P>
  <DL>
  <DT><B>Stage one</B></DT>
  <! Sec='12. Outline of Processing Steps' Level=0 Label='Stage' Line='Stage one'>
  <DD>The operations which may be performed in the first stage are badpixel
  correction, determination and subtraction of the readout bias level, and
  trimming. This stage is only performed if one or more of the <B>fixpix</B>,
  <B>overscan</B> or <B>trim</B> flags is set to yes.
  <P>
  First, all the calibration images which will be needed are identified. Any
  which were obtained in multi-readout mode AND which have not already been
  trimmed are selected for processing during this stage. This is necessary to
  ensure that the calibration images will be reduced properly. Similarly, the
  input list is searched and all multi-readout images, which have not already
  been trimmed are selected for processing.
  <P>
  The images selected in this way are then processed sequentially. Each is split
  into separate images one for each amplifier. The values of the trimsec and
  biassec header keywords for each of these sub-images are set as required. 
  <B>ccdproc</B> is then run to correct bad pixels, determine and subtract the
  readout bias and trim each sub-image. Finaly, the pieces are glued back 
  together again to form the complete image and the header information is 
  tidied up. The resulting image is initialy created as a temporary image.
  When stage one processing is complete the original image is deleted (or
  renamed using the specified backup prefix) and the corrected image replaces
  the original image.  Using a temporary image protects the data in the
  event of an abort or computer failure.  Keeping the original image name
  eliminates much of the record keeping and the need to generate new
  image names.
  </DD>
  </DL>
  <DL>
  <DT><B>Stage two</B></DT>
  <! Sec='12. Outline of Processing Steps' Level=0 Label='Stage' Line='Stage two'>
  <DD><B>Ccdproc</B> is now run a second time to process ALL input images. For those
  images which were NOT selected for processing during stage one all the selected
  processing steps are carried out during this second pass. For those which were
  selected in stage one only the remaining processing steps will be performed.
  Again the output processed image is initialy created as a temporary image.
  When stage two processing is complete the original image is deleted (or
  renamed using the specified backup prefix) and the corrected image replaces
  the original image.
  </DD>
  </DL>
  <P>
  The following difference in the behaviour of <B>quadprocfB and fBccdproc</B>
  should be noted:
  <DL>
  <DT><B></B></DT>
  <! Sec='12. Outline of Processing Steps' Level=0 Label='' Line=' '>
  <DD>Because it is a script, and because it is reads and writes each image several
  times during processing <B>quadproc</B> is not very efficiant. This will be 
  rectified when the present prototype code is replaced by the final version.
  </DD>
  </DL>
  <DL>
  <DT><B></B></DT>
  <! Sec='12. Outline of Processing Steps' Level=0 Label='' Line=' '>
  <DD>If backups are enable then <B>quadproc</B> will produce two intermediate 
  images for every input image which is modified in both processing stages.
  These backup images may quickly fill up the available disk space.
  </DD>
  </DL>
  <DL>
  <DT><B></B></DT>
  <! Sec='12. Outline of Processing Steps' Level=0 Label='' Line=' '>
  <DD>Images may not be processed in the order they appear in the input list. Stage
  one processing is performed (if necessary) on all calibration images, then on
  all images in the input list. Any images which have already been trimmed, or
  which were taken in mono-readout mode will be skipped. Stage two processing is 
  then done sequentially on all images in the input list.
  </DD>
  </DL>
  </UL>
  <! EndSection:   '12. Outline of Processing Steps'>
  <H3>13. processing arithmetic</H3>
  <! BeginSection: '13. Processing Arithmetic'>
  <UL>
  The <B>quadproc</B> task has two data paths, one for real image pixel datatypes
  and one for short integer pixel datatype.  In addition internal arithmetic
  is based on the rules of FORTRAN.  For efficiency there is
  no checking for division by zero in the flat field calibration.
  The following rules describe the processing arithmetic and data paths.
  <P>
  <DL>
  <DT><B>(1)</B></DT>
  <! Sec='13. Processing Arithmetic' Level=0 Label='' Line='(1)'>
  <DD>If the input, output, or any calibration image is of type real the
  real data path is used.  This means all image data is converted to
  real on input.  If all the images are of type short all input data
  is kept as short integers.  Thus, if all the images are of the same type
  there is no datatype conversion on input resulting in greater
  image I/O efficiency.
  </DD>
  </DL>
  <DL>
  <DT><B>(2)</B></DT>
  <! Sec='13. Processing Arithmetic' Level=0 Label='' Line='(2)'>
  <DD>In the real data path the processing arithmetic is always real and,
  if the output image is of short pixel datatype, the result
  is truncated.
  </DD>
  </DL>
  <DL>
  <DT><B>(3)</B></DT>
  <! Sec='13. Processing Arithmetic' Level=0 Label='' Line='(3)'>
  <DD>The overscan vector and the scale factors for dark count, flat field,
  iillumination, and fringe calibrations are always of type real.  Therefore,
  in the short data path any processing which includes these operations
  will be coerced to real arithmetic and the result truncated at the end
  of the computation.
  </DD>
  </DL>
  </UL>
  <! EndSection:   '13. Processing Arithmetic'>
  <H3>14. in the absence of image header information</H3>
  <! BeginSection: '14. In the Absence of Image Header Information'>
  <UL>
  The tasks in the <B>quad</B> package are most convenient to use when
  the CCD image type, subset, and exposure time are contained in the
  image header. This is true for all data obtained with Arcon.  The ability to
  redefine which header parameters contain this information makes it possible
  to use the package at many different observatories (see <B>instruments</B>). 
  However, in the absence of any image header information the tasks may still
  be used effectively.  There are two ways to proceed.  One way is to use
  <B>ccdhedit</B> to place the information in the image header.
  <P>
  The second way is to specify the processing operations more explicitly
  than is needed when the header information is present.  The parameter
  <I>ccdtype</I> is set to "<TT></TT>" or to "<TT>none</TT>".  The calibration images are
  specified explicitly by task parameter since they cannot be recognized
  in the input list.  Only one subset at a time may be processed.
  <P>
  If dark count and fringe corrections are to be applied the exposure
  times must be added to all the images.  Alternatively, the dark count
  and fringe images may be scaled explicitly for each input image.  This
  works because the exposure times default to 1 if they are not given in
  the image header.
  </UL>
  <! EndSection:   '14. In the Absence of Image Header Information'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The user's <B>guide</B> presents a tutorial in the use of this task.
  <P>
  1. In general all that needs to be done is to set the task parameters
  and enter
  <P>
  	cl&gt; quadproc *.imh &amp;
  <P>
  This will run in the background and process all images which have not
  been processed previously.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  quadformat, ccdproc, instruments, ccdtypes, flatfields, icfit, quad, guide,
  mkillumcor, mkskycor, mkfringecor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' '1. Parameters' '2. Fixpix' '3. Overscan' '4. Trim' '5. Zerocor' '6. Darkcor' '7. Flatcor' '8. Illumcor' '9. Fringecor' '10. Readcor' '11. Scancor' '12. Outline of Processing Steps' '13. Processing Arithmetic' '14. In the Absence of Image Header Information' 'EXAMPLES' 'SEE ALSO'  >
  
