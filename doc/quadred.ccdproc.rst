.. _ccdproc:

ccdproc — Process CCD images (including quadformat data)
========================================================

**Package: quadred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ccdproc -- Process CCD images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Synopsis</H3>
  <! BeginSection: 'SYNOPSIS'>
  <UL>
  This is the main processing task for CCD data in single image or
  <B>quadformat</B> image formats.
  </UL>
  <! EndSection:   'SYNOPSIS'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  ccdproc images
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
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>List of output images.  If no list is given then the processing will replace
  the input images with the processed images.  If a list is given it must
  match the input image list.  <I>Note that any dependent calibration images
  still be processed in-place with optional backup.</I>
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
  lines and columns?  If yes then a bad pixel mask, image, or file must be
  specified.
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
  <DD>Convert zero level, dark count and flat field images to scan mode flat
  field images?  If yes then the form of scan mode correction is specified by
  the parameter <I>scantype</I>.
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
  <DD>Bad pixel mask, image, or file.  If "<TT>image</TT>" is specified then the name is
  specified in the image header or instrument translation file.  If "<TT>BPM</TT>" is
  specified then the standard BPM image header keyword defines a bad pixel
  mask.  A bad pixel mask is a compact format ("<TT>.pl</TT>" extension) with zero
  values indicating good pixels and non-zero values indicating bad pixels.  A
  bad pixel image is a regular image in which zero values are good pixels and
  non-zero values are bad pixels.  A bad pixel file specifies bad pixels or
  rectangular bad pixel regions as described later.  The direction of
  interpolation is determined by the mask value with a value of two
  interpolating across columns, a value of three interpolating across lines,
  and any other non-zero value interpolating along the narrowest dimension.
  </DD>
  </DL>
  <DL>
  <DT><B>biassec</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='biassec' Line='biassec'>
  <DD>Overscan bias strip image section.  If "<TT>image</TT>" is specified then the overscan
  bias section is specified in the image header or instrument translation file.
  Only the part of the bias section along the readout axis is used.  The
  length of the bias region fit is defined by the trim section.  If one
  wants to limit the region of the overscan used in the fit to be less
  than that of the trim section then the sample region parameter,
  <I>sample</I>, should be used.  It is an error if no section or the
  whole image is specified.
  </DD>
  </DL>
  <DL>
  <DT><B>trimsec</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trimsec' Line='trimsec'>
  <DD>Image section for trimming.  If "<TT>image</TT>" is specified then the trim image
  section is specified in the image header or instrument translation file.
  However, for <I>quadformat</I> data this parameter is not used and the trim
  sections are assumed to be in the image header.
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
  replaced by this value.  This allows flat fields processed by <B>ccdproc</B>
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
  two dimensional image.  In this mode unscanned zero level, dark count and
  flat fields are numerically scanned to form scanned flat fields comparable
  to the observations.
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
  <DD>Number of object scan readout lines used in short scan mode.  This parameter
  is used when the scan type is "<TT>shortscan</TT>" and the number of scan lines
  cannot be determined from the object image header (using the keyword
  nscanrows or it's translation).
  </DD>
  </DL>
  <P>
  <P>
  <CENTER>OVERSCAN FITTING PARAMETERS
  
  </CENTER><BR>
  <P>
  There are two types of overscan (or prescan) determinations.  One determines
  a independent overscan value for each line  and is only available for a
  <I>readaxis</I> of 1.  The other averages the overscan along the readout
  direction to make an overscan vector, fits a smoothing function to the vector,
  and then evaluate and then evaluates the smooth function at each readout
  line or column.  The line-by-line determination only uses the
  <I>function</I> parameter and the smoothing determinations uses all
  the following parameters.
  <P>
  <DL>
  <DT><B>function = "<TT>legendre</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "legendre"'>
  <DD>Line-by-line determination of the overscan is specified by:
  <P>
  <PRE>
           mean - the mean of the biassec columns at each line
         median - the median of the biassec columns at each line
         minmax - the mean at each line with the min and max excluded
  </PRE>
  <P>
  The smoothed overscan vector may be fit by one of the functions:
  <P>
  <PRE>
       legendre - legendre polynomial
      chebyshev - chebyshev polynomial
        spline1 - linear spline
        spline3 - cubic spline
  </PRE>
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
  <DL>
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Fit the overscan vector interactively?  If yes and the overscan function type
  is one of the <B>icfit</B> types then the average overscan vector is fit
  interactively using the <B>icfit</B> package.  If no then the fitting parameters
  given below are used.
  </DD>
  </DL>
  <P>
  The parameters <I>verbose</I>, <I>logfile</I>, and <I>backup</I> default to
  the package parameters but may be specified to override the package
  values.  This is used by the <B>quadproc</B> script task.  These parameters
  are described in the help topic "<TT>quadred.package</TT>".
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Ccdproc</B> processes CCD images to correct and calibrate for
  detector defects, readout bias, zero level bias, dark counts,
  response, iillumination, and fringing.  It also trims unwanted
  lines and columns and changes the pixel datatype.  It is efficient
  and easy to use; all one has to do is set the parameters and then
  begin processing the images.  The task takes care of most of the
  record keeping and automatically does the prerequisite processing
  of calibration images.  Beneath this simplicity there is much that
  is going on.  In this section a simple description of the usage is
  given.  The following sections present more detailed discussions
  on the different operations performed and the order and logic
  of the processing steps.  For a user's guide to the <B>ccdred</B>
  package see <B>guide</B>.  Much of the ease of use derives from using
  information in the image header.  If this information is missing
  see section 13.
  <P>
  One begins by setting the task parameters.  There are many parameters
  but they may be easily reviewed and modified using the task <B>eparam</B>.
  The input CCD images to be processed are given as an image list.
  Previously processed images are ignored and calibration images are
  recognized, provided the CCD image types are in the image header (see
  <B>instruments</B> and <B>ccdtypes</B>).  Therefore it is permissible to
  use simple image templates such as "<TT>*.imh</TT>".  The <I>ccdtype</I> parameter
  may be used to select only certain types of CCD images to process
  (see <B>ccdtypes</B>).
  <P>
  The processing operations are selected by boolean (yes/no) parameters.
  Because calibration images are recognized and processed appropriately,
  the processing operations for object images should be set.
  Any combination of operations may be specified and the operations are
  performed simultaneously.  While it is possible to do operations in
  separate steps this is much less efficient.  Two of the operation
  parameters apply only to zero level and flat field images.  These
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
  which affect <B>ccdproc</B>.  These include the instrument and subset
  files, the text and plot log files, the output pixel datatype,
  the amount of memory available for calibration image caching,
  the verbose parameter for logging to the terminal, and the backup
  prefix.  These are described in <B>ccdred</B>.
  <P>
  Calibration images are specified by task parameters and/or in the
  input image list.  If more than one calibration image is specified
  then the first one encountered is used and a warning is issued for the
  extra images.  Calibration images specified by
  task parameters take precedence over calibration images in the input list.
  These images also need not have a CCD image type parameter since the task
  parameter identifies the type of calibration image.  This method is
  best if there is only one calibration image for all images
  to be processed.  This is almost always true for zero level and dark
  count images.  If no calibration image is specified by task parameter
  then calibration images in the input image list are identified and
  used.  This requires that the images have CCD image types recognized
  by the package.  This method is useful if one may simply say "<TT>*.imh</TT>"
  as the image list to process all images or if the images are broken
  up into groups, in "<TT>@</TT>" files for example, each with their own calibration
  frames.
  <P>
  When an input image is processed the task first determines the processing
  parameters and calibration images.  If a requested operation has been
  done it is skipped and if all requested operations have been completed then
  no processing takes place.  When it determines that a calibration image
  is required it checks for the image from the task parameter and then
  for a calibration image of the proper type in the input list.
  <P>
  Having
  selected a calibration image it checks if it has been processed by
  looking for the image header flag CCDPROC.  If it is not present then
  the calibration image is processed.  When any image has been processed
  the CCDPROC flag is added.  For images processed directly by <B>ccdproc</B>
  the individual processing flags are checked even if the CCDPROC flag is
  present.  However, the automatic processing of the calibration images is
  only done if the CCDPROC flag is absent!  This is to make the task more
  efficient by not having to check every flag for every calibration image
  for every input image.  Thus, if additional processing
  steps are added after images have been partially reduced then input images
  will be processed for the new steps but calibration images will not be
  processed automatically.
  <P>
  After the calibration images have been identified, and processed if
  necessary, the images may be cached in memory.  This is done when there
  are more than two input images (it is actually less efficient to
  cache the calibration images for one or two input images) and the parameter
  <I>max_cache</I> is greater than zero.  When caching, as many calibration
  images as allowed by the specified memory are read into memory and
  kept there for all the input images.  Cached images are, therefore,
  only read once from disk which reduces the amount of disk I/O.  This
  makes a modest decrease in the execution time.  It is not dramatic
  because the actual processing is fairly CPU intensive.
  <P>
  Once the processing parameters and calibration images have been determined
  the input image is processed for all the desired operations in one step;
  i.e. there are no intermediate results or images.  This makes the task
  efficient.  If a matching list of output images is given then the processed
  image is written to the specified output image name.  If no output image
  list is given then the corrected image is output as a temporary image until
  the entire image has been processed.  When the image has been completely
  processed then the original image is deleted (or renamed using the
  specified backup prefix) and the corrected image replaces the original
  image.  Using a temporary image protects the data in the event of an abort
  or computer failure.  Keeping the original image name eliminates much of
  the record keeping and the need to generate new image names.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>1. fixpix</H3>
  <! BeginSection: '1. Fixpix'>
  <UL>
  Regions of bad lines and columns may be replaced by linear
  interpolation from neighboring lines and columns when the parameter
  <I>fixpix</I> is set.  This algorithm is the same as used in the
  task <B>fixpix</B>.  The bad pixels may be specified by a pixel mask,
  an image, or a text file.  For the mask or image, values of zero indicate
  good pixels and other values indicate bad pixels to be replaced.
  <P>
  The text file consists of lines with four fields, the starting and
  ending columns and the starting and ending lines.  Any number of
  regions may be specified.  Comment lines beginning with the character
  <TT>'#'</TT> may be included.  The description applies directly to the input
  image (before trimming) so different files are needed for previously
  trimmed or subsection readouts.  The data in this file is internally
  turned into the same description as a bad pixel mask with values of
  two for regions which are narrower or equal across the columns and
  a value of three for regions narrower across lines.
  <P>
  The direction of interpolation is determined from the values in the
  mask, image, or the converted text file.  A value of two interpolates
  across columns, a value of three interpolates across lines, and any
  other value interpolates across the narrowest dimension of bad pixels
  and using column interpolation if the two dimensions are equal.
  <P>
  The bad pixel description may be specified explicitly with the parameter
  <I>fixfile</I> or indirectly if the parameter has the value "<TT>image</TT>".  In the
  latter case the instrument file must contain the name of the file.
  </UL>
  <! EndSection:   '1. Fixpix'>
  <H3>2. overscan</H3>
  <! BeginSection: '2. Overscan'>
  <UL>
  If an overscan or prescan correction is specified (<I>overscan</I>
  parameter) then the image section (<I>biassec</I> parameter) defines
  the overscan region.
  <P>
  There are two types of overscan (or prescan) determinations.  One determines
  a independent overscan value for each line  and is only available for a
  <I>readaxis</I> of 1.  The other averages the overscan along the readout
  direction to make an overscan vector, fits a smoothing function to the vector,
  and then evaluate and then evaluates the smooth function at each readout
  line or column.
  <P>
  The line-by-line determination provides an mean, median, or
  mean with the minimum and maximum values excluded.  The median
  is lowest value of the middle two when the number of overscan columns
  is even rather than the mean.
  <P>
  The smoothed overscan vector determination uses the <B>icfit</B> options
  including interactive fitting.  The fitting function is generally either a
  constant (polynomial of 1 term) or a high order function which fits the
  large scale shape of the overscan vector.  Bad pixel rejection is also
  available to eliminate cosmic ray events.  The function fitting may be done
  interactively using the standard <B>icfit</B> iteractive graphical curve
  fitting tool.  Regardless of whether the fit is done interactively, the
  overscan vector and the fit may be recorded for later review in a metacode
  plot file named by the parameter <I>ccdred.plotfile</I>.  The mean value of
  the bias function is also recorded in the image header and log file.
  </UL>
  <! EndSection:   '2. Overscan'>
  <H3>3. trim</H3>
  <! BeginSection: '3. Trim'>
  <UL>
  When the parameter <I>trim</I> is set the input image will be trimmed to
  the image section given by the parameter <I>trimsec</I>.  This trim
  should, of course, be the same as that used for the calibration images.
  </UL>
  <! EndSection:   '3. Trim'>
  <H3>4. zerocor</H3>
  <! BeginSection: '4. Zerocor'>
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
  <! EndSection:   '4. Zerocor'>
  <H3>5. darkcor</H3>
  <! BeginSection: '5. Darkcor'>
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
  <! EndSection:   '5. Darkcor'>
  <H3>6. flatcor</H3>
  <! BeginSection: '6. Flatcor'>
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
  <B>ccdproc</B>.
  </UL>
  <! EndSection:   '6. Flatcor'>
  <H3>7. illumcor</H3>
  <! BeginSection: '7. Illumcor'>
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
  <! EndSection:   '7. Illumcor'>
  <H3>8. fringecor</H3>
  <! BeginSection: '8. Fringecor'>
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
  <! EndSection:   '8. Fringecor'>
  <H3>9. readcor</H3>
  <! BeginSection: '9. Readcor'>
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
  <! EndSection:   '9. Readcor'>
  <H3>10. scancor</H3>
  <! BeginSection: '10. Scancor'>
  <UL>
  CCD detectors may be operated in several modes in astronomical
  applications.  The most common is as a direct imager where each pixel
  integrates one point in the sky or spectrum.  However, the design of most CCD's
  allows the sky to be scanned across the CCD while shifting the
  accumulating signal at the same rate.  <B>Ccdproc</B> provides for two
  scanning modes called "<TT>shortscan</TT>" and "<TT>longscan</TT>".  The type of scan
  mode is set with the parameter <I>scanmode</I>.
  <P>
  In "<TT>shortscan</TT>" mode the detector is scanned over a specified number of
  lines (not necessarily at sideral rates).  The lines that scroll off the
  detector during the integration are thrown away.  At the end of the
  integration the detector is read out in the same way as an unscanned
  observation.  The advantage of this mode is that the small scale, zero
  level, dark count and flat field responses are averaged in one dimension
  over the number of lines scanned.  A zero level, dark count or flat field may be
  observed in the same way in which case there is no difference in the
  processing from unscanned imaging and the parameter <I>scancor</I> may be
  no.  If it is yes, though, checking is done to insure that the calibration
  image used has the same number of scan lines as the object being
  processed.  However, one obtains an increase in the statistical accuracy of
  if they are not scanned during the observation but
  digitally scanned during the processing.  In shortscan mode with
  <I>scancor</I> set to yes, zero level, dark count and flat field images are
  digitally scanned, if needed, by the same number of scan lines as the
  object.  The number of scan lines is determined from the object image
  header using the keyword nscanrow (or it's translation).  If not found the
  object is assumed to have been scanned with the value given by the
  <I>nscan</I> parameter.  Zero, dark and flat calibration images are assumed
  to be unscanned if the header keyword is not found.
  <P>
  If a scanned zero level, dark count or flat field image is not found
  matching the object then one may be created from the unscanned calibration
  image.  The image will have the root name of the unscanned image with an
  extension of the number of scan rows; i.e. Flat1.32 is created from Flat1
  with a digital scanning of 32 lines.
  <P>
  In "<TT>longscan</TT>" mode the detector is continuously read out to produce an
  arbitrarily long strip.  Provided data which has not passed over the entire
  detector is thrown away, the zero level, dark count, and flat field
  corrections will be one dimensional.  If <I>scancor</I> is specified and the
  scan mode is "<TT>longscan</TT>" then a one dimensional zero level, dark count, and
  flat field correction will be applied.
  </UL>
  <! EndSection:   '10. Scancor'>
  <H3>11. processing steps</H3>
  <! BeginSection: '11. Processing Steps'>
  <UL>
  The following describes the steps taken by the task.  This detailed
  outline provides the most detailed specification of the task.
  <P>
  <DL>
  <DT><B>(1)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(1)'>
  <DD>An image to be processed is first checked that it is of the specified
  CCD image type.  If it is not the desired type then go on to the next image.
  </DD>
  </DL>
  <DL>
  <DT><B>(2)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(2)'>
  <DD>A temporary output image is created of the specified pixel data type
  (<B>ccdred.pixeltype</B>).  The header parameters are copied from the
  input image.
  </DD>
  </DL>
  <DL>
  <DT><B>(3)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(3)'>
  <DD>If trimming is specified and the image has not been trimmed previously,
  the trim section is determined.
  </DD>
  </DL>
  <DL>
  <DT><B>(4)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(4)'>
  <DD>If bad pixel replacement is specified and this has not been done
  previously, the bad pixel file is determined either from the task
  parameter or the instrument translation file.  The bad pixel regions
  are read.  If the image has been trimmed previously and the bad pixel
  file contains the word "<TT>untrimmed</TT>" then the bad pixel coordinates are
  translated to those of the trimmed image.
  </DD>
  </DL>
  <DL>
  <DT><B>(5)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(5)'>
  <DD>If an overscan correction is specified and this correction has not been
  applied, the overscan section is averaged along the readout axis.  If
  trimming is to be done the overscan section is trimmed to the same
  limits.  A function is fit either interactively or noninteractively to
  the overscan vector.  The function is used to produce the overscan
  vector to be subtracted from the image.  This is done in real
  arithmetic.
  </DD>
  </DL>
  <DL>
  <DT><B>(6)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(6)'>
  <DD>If the image is a zero level image go to processing step 12.
  If a zero level correction is desired and this correction has not been
  performed, find the zero level calibration image.  If the zero level
  calibration image has not been processed it is processed at this point.
  This is done by going to processing step 1 for this image.  After the
  calibration image has been processed, processing of the input image
  continues from this point.
  The processed calibration image may be
  cached in memory if it has not been previously and if there is enough memory.
  </DD>
  </DL>
  <DL>
  <DT><B>(7)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(7)'>
  <DD>If the image is a dark count image go to processing step 12.
  If a dark count correction is desired and this correction has not been
  performed, find the dark count calibration image.  If the dark count
  calibration image has not been processed it is processed at this point.
  This is done by going to processing step 1 for this image.  After the
  calibration image has been processed, processing of the input image
  continues from this point.  The ratio of the input image dark time
  to the dark count image dark time is determined to be multiplied with
  each pixel of the dark count image before subtracting from the input
  image.
  The processed calibration image may be
  cached in memory if it has not been previously and if there is enough memory.
  </DD>
  </DL>
  <DL>
  <DT><B>(8)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(8)'>
  <DD>If the image is a flat field image go to processing step 12.  If a flat
  field correction is desired and this correction has not been performed,
  find the flat field calibration image of the appropriate subset.  If
  the flat field calibration image has not been processed it is processed
  at this point.  This is done by going to processing step 1 for this
  image.  After the calibration image has been processed, processing of
  the input image continues from this point.  The mean of the image
  is determined from the image header to be used for scaling.  If no
  mean is found then a unit scaling is used.
  The processed calibration image may be
  cached in memory if it has not been previously and if there is enough memory.
  </DD>
  </DL>
  <DL>
  <DT><B>(9)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(9)'>
  <DD>If the image is an iillumination image go to processing step 12.  If an
  iillumination correction is desired and this correction has not been performed,
  find the iillumination calibration image of the appropriate subset.
  The iillumination image must have the "<TT>mkillum</TT>" processing flag or the
  <B>ccdproc</B> will abort with an error.  The mean of the image
  is determined from the image header to be used for scaling.  If no
  mean is found then a unit scaling is used.  The processed calibration
  image may be
  cached in memory if it has not been previously and there is enough memory.
  </DD>
  </DL>
  <DL>
  <DT><B>(10)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(10)'>
  <DD>If the image is a fringe image go to processing step 12.  If a fringe
  correction is desired and this correction has not been performed,
  find the fringe calibration image of the appropriate subset.
  The iillumination image must have the "<TT>mkfringe</TT>" processing flag or the
  <B>ccdproc</B> will abort with an error.  The ratio of the input
  image exposure time to the fringe image exposure time is determined.
  If there is a fringe scaling in the image header then this factor
  is multiplied by the exposure time ratio.  This factor is used
  for scaling.  The processed calibration image may be
  cached in memory if it has not been previously and there is enough memory.
  </DD>
  </DL>
  <DL>
  <DT><B>(11)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(11)'>
  <DD>If there are no processing operations flagged, delete the temporary output
  image, which has been opened but not used, and go to 14.
  </DD>
  </DL>
  <DL>
  <DT><B>(12)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(12)'>
  <DD>The input image is processed line by line with trimmed lines ignored.
  A line of the input image is read.  Bad pixel replacement and trimming
  is applied to the image.  Image lines from the calibration images
  are read from disk or the image cache.  If the calibration is one
  dimensional (such as a readout zero
  level correction or a longscan flat field correction) then the image
  vector is read only once.  Note that IRAF image I/O is buffered for
  efficiency and accessing a line at a time does not mean that image
  lines are read from disk a line at a time.  Given the input line, the
  calibration images, the overscan vector, and the various scale factors
  a special data path for each combination of corrections is used to
  perform all the processing in the most efficient manner.  If the
  image is a flat field any pixels less than the <I>minreplace</I>
  parameter are replaced by that minimum value.  Also a mean is
  computed for the flat field and stored as the CCDMEAN keyword and
  the time, in a internal format, when this value was calculated is stored
  in the CCDMEANT keyword.  The time is checked against the image modify
  time to determine if the value is valid or needs to be recomputed.
  </DD>
  </DL>
  <DL>
  <DT><B>(13)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(13)'>
  <DD>The input image is deleted or renamed to a backup image.  The temporary
  output image is renamed to the input image name.
  </DD>
  </DL>
  <DL>
  <DT><B>(14)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(14)'>
  <DD>If the image is a zero level image and the readout correction is specified
  then it is averaged to a one dimensional readout correction.
  </DD>
  </DL>
  <DL>
  <DT><B>(15)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(15)'>
  <DD>If the image is a zero level, dark count, or flat field image and the scan
  mode correction is specified then the correction is applied.  For shortscan
  mode a modified two dimensional image is produced while for longscan mode a
  one dimensional average image is produced.
  </DD>
  </DL>
  <DL>
  <DT><B>(16)</B></DT>
  <! Sec='11. Processing Steps' Level=0 Label='' Line='(16)'>
  <DD>The processing is completed and either the next input image is processed
  beginning at step 1 or, if it is a calibration image which is being
  processed for an input image, control returns to the step which initiated
  the calibration image processing.
  </DD>
  </DL>
  </UL>
  <! EndSection:   '11. Processing Steps'>
  <H3>12. processing arithmetic</H3>
  <! BeginSection: '12. Processing Arithmetic'>
  <UL>
  The <B>ccdproc</B> task has two data paths, one for real image pixel datatypes
  and one for short integer pixel datatype.  In addition internal arithmetic
  is based on the rules of FORTRAN.  For efficiency there is
  no checking for division by zero in the flat field calibration.
  The following rules describe the processing arithmetic and data paths.
  <P>
  <DL>
  <DT><B>(1)</B></DT>
  <! Sec='12. Processing Arithmetic' Level=0 Label='' Line='(1)'>
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
  <! Sec='12. Processing Arithmetic' Level=0 Label='' Line='(2)'>
  <DD>In the real data path the processing arithmetic is always real and,
  if the output image is of short pixel datatype, the result
  is truncated.
  </DD>
  </DL>
  <DL>
  <DT><B>(3)</B></DT>
  <! Sec='12. Processing Arithmetic' Level=0 Label='' Line='(3)'>
  <DD>The overscan vector and the scale factors for dark count, flat field,
  iillumination, and fringe calibrations are always of type real.  Therefore,
  in the short data path any processing which includes these operations
  will be coerced to real arithmetic and the result truncated at the end
  of the computation.
  </DD>
  </DL>
  </UL>
  <! EndSection:   '12. Processing Arithmetic'>
  <H3>13. in the absence of image header information</H3>
  <! BeginSection: '13. In the Absence of Image Header Information'>
  <UL>
  The tasks in the <B>ccdred</B> package are most convenient to use when
  the CCD image type, subset, and exposure time are contained in the
  image header.  The ability to redefine which header parameters contain
  this information makes it possible to use the package at many different
  observatories (see <B>instruments</B>).  However, in the absence of any
  image header information the tasks may still be used effectively.
  There are two ways to proceed.  One way is to use <B>ccdhedit</B>
  to place the information in the image header.
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
  <! EndSection:   '13. In the Absence of Image Header Information'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The user's <B>guide</B> presents a tutorial in the use of this task.
  <P>
  1. In general all that needs to be done is to set the task parameters
  and enter
  <P>
  	cl&gt; ccdproc *.imh &amp;
  <P>
  This will run in the background and process all images which have not
  been processed previously.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  package, quadformat, instruments, ccdtypes, flatfields, icfit, ccdred,
  guide, mkillumcor, mkskycor, mkfringecor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SYNOPSIS' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' '1. Fixpix' '2. Overscan' '3. Trim' '4. Zerocor' '5. Darkcor' '6. Flatcor' '7. Illumcor' '8. Fringecor' '9. Readcor' '10. Scancor' '11. Processing Steps' '12. Processing Arithmetic' '13. In the Absence of Image Header Information' 'EXAMPLES' 'SEE ALSO'  >
  
