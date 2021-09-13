peak — Fit the psf to single stars
==================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>peak (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>peak (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>peak</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  peak -- fit the PSF model to single stars
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  peak image photfile psfimage peakfile rejfile
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images containing the stars to be fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_photfile">photfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photfile' Line='photfile'>
  <DD>The list of input photometry files containing initial estimates of the
  positions and magnitudes of the stars to be fit. The number of photometry
  files must be equal to the number of input images. If photfile is "<TT>default</TT>",
  "<TT>dir$default</TT>", or a directory specification  PSF searches for a file called
  dir$image.mag.# where # is the highest available version number for the file.
  Photfile is usually the output of the DAOPHOT PHOT task, but may also be the
   output of PEAK itself, or of the DAOPHOT package GROUP, NSTAR,  ALLSTAR or
  PSF tasks. Photfile may be an APPHOT/DAOPHOT text database or an STSDAS table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_psfimage">psfimage</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='psfimage' Line='psfimage'>
  <DD>The list of images containing the PSF models computed by the DAOPHOT PSF task.
  The number of PSF images must be equal to the number of input images.  If
  psfimage is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification,
  then PEAK will look for an image with the name image.psf.?, where
  ? is the highest existing version number.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_peakfile">peakfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='peakfile' Line='peakfile'>
  <DD>The list of output photometry files. There must be one output photometry
  file for every input image.  If peakfile is "<TT>default</TT>", "<TT>dir$default</TT>", or a
  directory specification, then PEAK will write an output file with the name
  image.pk.? where ? is the next available version number. Peakfile is a text
  database if the DAOPHOT package parameter text is "<TT>yes</TT>", an STSDAS table
  database if it is "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rejfile">rejfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rejfile' Line='rejfile'>
  <DD>The list of output rejected photometry files containing the positions and sky
  values of stars that could not be fit. If rejfile is undefined, results for all
  the stars in photfile are written to <I>peakfile</I>, otherwise only the stars
  which were successfully fit are written to <I>peakfile</I> and the remainder are
  written to rejfile. If rejfile is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory
  specification PEAK writes an output file with the name image.prj.? where ? is
  the next available version number. Otherwise rejfile must specify one output
  photometry file for every input image. Rejfile is a text database if the
  DAOPHOT package parameter <I>text</I> is "<TT>yes</TT>", an STSDAS binary table database
  if it is "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_datapars">datapars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""'>
  <DD>The name of the file containing the data dependent parameters. The parameters
  <I>scale</I>, <I>datamin</I>, and <I>datamax</I> are located here. If datapars
  is undefined then the default parameter set in uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_daopars">daopars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='daopars' Line='daopars = ""'>
  <DD>The name of the file containing the daophot fitting parameters. The parameters
  <I>psfrad</I> and <I>fitrad</I> are located here. If <I>daopars</I> is undefined
  then the default parameter set in uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcsin">wcsin = "<TT>)_.wcsin</TT>", wcsout = "<TT>)_.wcsout</TT>", wcspsf = "<TT>)_.wcspsf</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsin' Line='wcsin = ")_.wcsin", wcsout = ")_.wcsout", wcspsf = ")_.wcspsf"'>
  <DD>The coordinate system of the input coordinates read from <I>photfile</I>, of the
  psf model <I>psfimage</I>, and of the output coordinates written to
  <I>peakfile</I> and <I>rejfile</I> respectively. The image header coordinate
  system is used to transform from the input coordinate system to the "<TT>logical</TT>"
  pixel coordinate system used internally, from the internal logical system to
  the PSF model system, and from the internal "<TT>logical</TT>" pixel coordinate system
  to the output coordinate system. The input coordinate system options are
  "<TT>logical</TT>", "<TT>tv</TT>", "<TT>physical</TT>", and "<TT>world</TT>". The PSF model and output coordinate
  system options are "<TT>logical</TT>", "<TT>tv</TT>", and "<TT>physical</TT>". The image cursor coordinate
  system is assumed to be the "<TT>tv</TT>" system.
  <DL>
  <DT><B><A NAME="l_logical">logical</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='logical' Line='logical'>
  <DD>Logical coordinates are pixel coordinates relative to the current image.
  The  logical coordinate system is the coordinate system used by the image
  input/output routines to access the image data on disk. In the logical
  coordinate system the coordinates of the first pixel of a  2D image, e.g.
  dev$ypix  and a 2D image section, e.g. dev$ypix[200:300,200:300] are
  always (1,1).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_tv">tv</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='tv' Line='tv'>
  <DD>Tv coordinates are the pixel coordinates used by the display servers. Tv
  coordinates  include  the effects of any input image section, but do not
  include the effects of previous linear transformations. If the input
  image name does not include an image section, then tv coordinates are
  identical to logical coordinates.  If the input image name does include a
  section, and the input image has not been linearly transformed or copied from
  a parent image, tv coordinates are identical to physical coordinates.
  In the tv coordinate system the coordinates of the first pixel of a
  2D image, e.g. dev$ypix and a 2D image section, e.g. dev$ypix[200:300,200:300]
  are (1,1) and (200,200) respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_physical">physical</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='physical' Line='physical'>
  <DD>Physical coordinates are pixel coordinates invariant  with respect to linear
  transformations of the physical image data.  For example, if the current image
  was created by extracting a section of another image,  the  physical
  coordinates of an object in the current image will be equal to the physical
  coordinates of the same object in the parent image,  although the logical
  coordinates will be different.  In the physical coordinate system the
  coordinates of the first pixel of a 2D image, e.g. dev$ypix and a 2D
  image section, e.g. dev$ypix[200:300,200:300] are (1,1) and (200,200)
  respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_world">world</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='world' Line='world'>
  <DD>World coordinates are image coordinates in any units which are invariant
  with respect to linear transformations of the physical image data. For
  example, the ra and dec of an object will always be the same no matter
  how the image is linearly transformed. The units of input world coordinates
  must be the same as those expected by the image header wcs, e. g.
  degrees and degrees for celestial coordinate systems.
  </DD>
  </DL>
  The wcsin, wcspsf, and wcsout parameters default to the values of the package
  parameters of the same name. The default values of the package parameters
  wcsin, wcspsf,  and wcsout are "<TT>logical</TT>", "<TT>physical</TT>" and "<TT>logical</TT>" respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cache">cache = "<TT>)_.cache</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = ")_.cache"'>
  <DD>Cache the image pixels in memory. Cache may be set to the value of the apphot
  package parameter (the default), "<TT>yes</TT>", or "<TT>no</TT>". By default caching is
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verify">verify = "<TT>)_.verify</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = ")_.verify"'>
  <DD>Verify the critical PEAK task parameters? Verify can be set to the DAOPHOT
  package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = "<TT>)_.update</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = ")_.update"'>
  <DD>Update the PEAK task parameters if <I>verify</I> is "<TT>yes</TT>"? Update can be
  set to the default daophot package parameter value, "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = "<TT>)_.verbose</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages about the progress of the task ? Verbose can be set to the
  DAOPHOT package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  PEAK computes x and y centers, sky values  and magnitudes for all the stars in
  <I>photfile</I> by fitting the PSF model in <I>psfimage</I> to single stars in
  <I>image</I>. PEAK reads initial estimates of the centers and magnitudes along
  with the sky values from the photometry file <I>photfile</I>. <I>Photfile</I> is
  usually the output of the DAOPHOT PHOT task but may also be the output of PEAK
  itself, NSTAR, ALLSTAR, GROUP or PSF. The computed centers, sky values, and
  magnitudes are written to <I>peakfile</I> along with the number of iterations
  it took to fit the star, the goodness of fit statistic chi, and the image
  sharpness statistic sharp.  If <I>rejfile</I> is defined only stars that are
  successfully fit are written to <I>peakfile</I>. The remainder are written to
  <I>rejfile</I>. Otherwise all the stars are written to <I>peakfile</I>.
  <I>Peakfile</I> and <I>rejfile</I> are APPHOT/DAOPHOT text databases if the
  DAOPHOT package parameter <I>text</I> is "<TT>yes</TT>", STSDAS binary table databases
  if it is "<TT>no</TT>".
  <P>
  The coordinates read from <I>photfile</I> are assumed to be in coordinate
  system defined by <I>wcsin</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>", "<TT>physical</TT>",
  and "<TT>world</TT>" and the transformation from the input coordinate system to the
  internal "<TT>logical</TT>" system is defined by the image coordinate system. The
  simplest default is the "<TT>logical</TT>" pixel system. Users working on with image
  sections but importing pixel coordinate lists generated from the parent image
  must use the "<TT>tv</TT>" or "<TT>physical</TT>" input coordinate systems.
  <P>
  The coordinate system of the PSF model is the coordinate system defined by the
  <I>wcspsf</I> parameter. Normally the PSF model was derived from the input image
  and this parameter default to "<TT>logical</TT>". However if the PSF model was derived
  from a larger image which is a "<TT>parent</TT>" of the input image, then wcspsf should
  be set to "<TT>tv</TT>" or "<TT>physical</TT>" depending on the circumstances.
  <P>
  The coordinates written to <I>peakfile</I> and <I>rejfile</I> are in the
  coordinate system defined by <I>wcsout</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>",
  and "<TT>physical</TT>". The simplest default is the "<TT>logical</TT>" system. Users wishing to
  correlate the output coordinates of objects measured in image sections or
  mosaic pieces with coordinates in the parent image must use the "<TT>tv</TT>" or
  "<TT>physical</TT>" coordinate systems.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the input image pixels are cached in memory. If caching
  is enabled and the first measurement will appear to take a long time as the
  entire image must be read in before the measurement is actually made. All
  subsequent measurements will be very fast because PEAK is accessing memory not
  disk. The point of caching is to speed up random image access by making the
  internal image i/o buffers the same size as the image itself. However if the
  input object lists are sorted in row order and sparse caching may actually
  worsen not improve the execution time. Also at present there is no point in
  enabling caching for images that are less than or equal to 524288 bytes, i.e.
  the size of the test image dev$ypix, as the default image i/o buffer is exactly
  that size. However if the size of dev$ypix is doubled by converting it to a
  real image with the chpixtype task then the effect of caching in interactive
  is can be quite noticeable if measurements of objects in the top and bottom
  halves of the image are alternated.
  <P>
  By default PEAK computes new centers for all the stars in <I>photfile</I>.
  However if the DAOPARS parameter <I>recenter</I> is "<TT>no</TT>", PEAK assumes that the
  x and y centers in <I>photfile</I> are the true centers and does not refit them.
  This option can be quite useful in cases where accurate center values have been
  derived from an image that has been through some non-linear image restoration
  algorithm, but the photometry must be derived from the original unrestored
  image.
  <P>
  By default PEAK uses the sky value in <I>photfile</I>. However if the DAOPARS
  parameter <I>fitsky</I> is "<TT>yes</TT>", then PEAK computes a new sky value as part of
  the non-linear least-squares fit. Recomputing the sky can significantly reduce
  the scatter in the magnitudes in regions where the sky background is varying
  rapidly, but users may need to increase the <I>fitrad</I> parameter to include
  more sky pixels in the fit. Users should experiment cautiously with this option.
  <P>
  Only pixels within the good data range delimited by the DATAPARS task parameters
  <I>datamin</I> and <I>datamax</I> are included in the fit.  Most users set
  <I>datamin</I> and <I>datamax</I>  to exclude pixels outside the linearity
  regime of the detector. By default all the data is fit.  Users are advised to
  determine the values of these parameters for their detector and set the values
  in DATAPARS before beginning DAOPHOT reductions.
  <P>
  Only pixels within the fitting radius set by the DAOPARS task parameter
  <I>fitrad</I> divided by the DATAPARS parameter <I>scale</I> are included in the
  fit. Since the non-linear least-squares fits determine three unknowns, the x
  and y position of the star's centroid and its brightness, the value of
  <I>fitrad</I> must be sufficiently large to include at least three pixels in
  the fit.  To accelerate the convergence of the non-linear least-squares fitting
  algorithm, pixels within <I>fitrad</I> are assigned weights which are inversely
  proportional to the radial distance of the pixel from the x and y centroid of
  the star, falling from a maximum at the centroid to zero at the fitting radius.
  <I>Fitrad</I> must be sufficiently large to include at least three pixels with
  non-zero weights in the fit. Values of <I>fitrad</I> close to the full-width at
  half-maxima of the PSF are recommended.
  <P>
  PEAK performs a weighted fit to the PSF. The weight of each pixel is computed
  by combining the radial weighting function described above with weights derived
  from the expected random errors computed using the values of the DATAPARS
  parameters <I>readnoise</I> and <I>epadu</I> specified by the user. Both to
  obtain optimal fits, and because PEAK employs a conservative formula, dependent
  on <I>readnoise</I> and <I>epadu</I>, for reducing the weights of deviant pixels
  which do not approach the model as the fit proceeds, users are strongly
  advised to determine the values of these parameters accurately, and to enter
  these values in DATAPARS before beginning any DAOPHOT reductions.
  <P>
  For each star to be fit, PEAK extracts a subraster from <I>image</I> which is N
  by N pixels square where N is approximately 2 * <I>psfrad</I> / <I>scale</I>  + 1
  pixels wide. <I>Psfrad</I> is the PSF radius specified in the DAOPARS task and
  <I>scale</I> is the scale factor specified in the DATAPARS task. <I>Psfrad</I> may
  be less than or equal to, but can never exceed the value of the image header
  parameter "<TT>PSFRAD</TT>" in <I>psfimage</I>. <I>Psfrad</I> should be set to a value
  several pixels larger than <I>fitrad</I> in order to permit the x and y
  centroids to wander during the fitting process.
  <P>
  Along with the computed x and y centers and magnitudes, PEAK outputs the number
  of times the PSF fit had to be iterated to reach convergence for each star. The
  minimum number of iterations is three. The maximum number of iteration permitted
  is specified by the <I>maxiter</I> parameter in the DAOPARS task.  Obviously the
  results for stars which have reached the maximum iteration count should be
  viewed with suspicion. However since the convergence criteria are quite strict,
  (the computed magnitude must change  by less than .001 magnitudes or 0.05 sigma
  whichever is larger and the x and y centroids must change by less than 0.01
  pixels from one iteration to the next), even these stars may be reasonably well
  measured.
  <P>
  PEAK computes a goodness of fit statistic chi which is essentially the ratio of
  the observed pixel-to-pixel scatter in the fit residuals to the expected
  scatter. Since the expected scatter is dependent on the DATAPARS task parameters
  <I>readnoise</I> and <I>epadu</I>, it is important for these values to be set
  correctly. A plot of chi versus magnitude should scatter around unity with
  little or no trend in chi with magnitude, except at the bright end where
  saturation effects may be present.
  <P>
  Finally PEAK computes the statistic sharp which estimates the intrinsic angular
  size of the measured object outside the atmosphere. Sharp is roughly defined as
  the difference between the square of the width of the object and the square of
  the width of PSF. Sharp has values close to zero for single stars, large
  positive values for blended doubles and partially resolved galaxies, and large
  negative values for cosmic rays and blemishes.
  <P>
  Because PEAK cannot fit stars in crowded fields with overlapped images like the
  NSTAR and ALLSTAR  tasks do, and for sparsely populated frames aperture
  photometry produced by PHOT is often just as good and faster to compute, PEAK
  has few unique functions. PEAK is often useful however for fitting and removing
  single stars in images where the stars are interfering with the real object of
  interest such as a galaxy. In that case the PEAK results can be input to SUBSTAR
  which will then remove the interfering stars. Another potential use of PEAK
  is the removal of stars from sparsely populated sky flats in preparation
  for smoothing.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_output">OUTPUT</A></H2>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  If <I>verbose</I> = yes, a single line is output to the terminal for each star
  fit or rejected. Full output is written to <I>allstarfile</I> and <I>rejfile</I>.
  At the beginning of these two files a header listing the current values of the
  parameters is written. For each star fit/rejected the following quantities are
  written to the output file.
  <P>
  <PRE>
  	id  xcenter  ycenter  mag  merr  msky  niter  sharpness  chi
  	    pier  perr
  </PRE>
  <P>
  Id is the id number of the star. Xcenter and ycenter are the fitted coordinates
  in pixels. Mag and merr are the fitted magnitude and magnitude error
  respectively. Msky is the individual sky value for the star. Niter is the
  number of iterations it took to fit the star and sharpness and chi are the
  sharpness and goodness of fit statistic respectively. Pier and perror are the
  photometry error code and accompanying error message respectively.
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H2><A NAME="s_errors">ERRORS</A></H2>
  <! BeginSection: 'ERRORS'>
  <UL>
  <P>
  If no errors occur during the fitting process then pier is 0. Non-zero
  values of pier flag the following error conditions.
  <P>
  <PRE>
  	0		# No error
  	1		# The sky is undefined
  	2		# There are too few good pixels to fit the star
  	3		# The fit is singular
  	4		# The star is too faint
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ERRORS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <P>
  1. Compute the PSF model for the test image dev$ypix. Good stars for making the
  PSF model can be found at (442,410), (348,189), and (379,67).
  <P>
  <P>
  <PRE>
     da&gt; datapars.epadu = 14.0
     da&gt; datapars.readnoise = 75.0
  <P>
         ... set the gain and readout noise for the detector
  <P>
     da&gt; daofind dev$ypix default fwhmpsf=2.5 sigma=5.0 threshold=20.0
  <P>
          ... answer verify prompts
  <P>
          ... find stars in the image
  <P>
          ... answer will appear in ypix.coo.1
  <P>
      da&gt; phot dev$ypix default default annulus=10. dannulus=5.       \<BR>
          apertures = 3.0
  <P>
          ... answer verify prompts
  <P>
          ... do aperture photometry on the detected stars
  <P>
          ... answer will appear in ypix.mag.1
  <P>
      da&gt; display dev$ypix 1
  <P>
      da&gt; psf dev$ypix default "" default default default psfrad=11.0 \<BR>
          fitrad=3.0 mkstars=yes display=imdr
  <P>
          ... verify the critical parameters
  <P>
          ... move the image cursor to a candidate star and hit the a key,
              a plot of the stellar data appears
  <P>
          ... type ? for a listing of the graphics cursor menu
  <P>
          ... type a to accept the star, d to reject it
  <P>
          ... move to the next candidate stars and repeat the previous
              steps
  <P>
          ... type l to list all the psf stars
  <P>
          ... type f to fit the psf
  <P>
          ... move cursor to first psf star and type s to see residuals,
              repeat for all the psf stars
  <P>
          ... type w to save the PSF model
  <P>
          ... type q to quit, and q again to confirm
  <P>
          ... the output will appear in ypix.psf.1.imh, ypix.pst.1 and
              ypix.psg.1
  <P>
      da&gt; peak dev$ypix default default default default 
  <P>
  	... the results will appear in ypix.pk.1 and ypix.prj.1
  <P>
      da&gt; pdump ypix.pk.1 sharpness,chi yes | graph
  <P>
  	... plot chi versus sharpness, the stars should cluster around
  	    sharpness = 0.0 and chi = 1.0, note that the frame does
  	    not have a lot of stars
  <P>
      da&gt; substar dev$ypix ypix.pk.1 "" default default
  <P>
  	... subtract the fitted stars
  <P>
      da&gt; display ypix.sub.1 2 
  <P>
  	... note that the psf stars subtract reasonably well but other
  	    objects which are not stars don't
  </PRE>
  <P>
  <P>
  2. Run peak on a section of the input image using the photometry file and PSF
  model derived in example 1 for the parent image and writing the results
  in the coordinate system of the parent image.
  <P>
  <PRE>
      da&gt; peak dev$ypix[150:450,150:450] default default default default \<BR>
          wcsin=tv wcspsf=tv wcsout=tv 
  <P>
  	... answer the verify prompts
  <P>
  	... fit the stars
  <P>
  	... the results will appear in ypix.pk.2 and ypix.prj.2
  <P>
      da&gt; display dev$ypix[150:450,150:450] 1
  <P>
  	... display the image
  <P>
      da&gt; pdump ypix.pk.2 xc,yc yes | tvmark 1 STDIN col=204
  <P>
  	... mark the stars
  <P>
      da&gt; substar dev$ypix ypix.pk.2 "" default default 
  <P>
  	... subtract stars from parent image
  <P>
  	... the output images is ypix.sub.2
  <P>
  <P>
      da&gt; substar dev$ypix[150:450,150:450] ypix.pk.2 "" default default  \<BR>
  	wcsin=tv wcspsf=tv wcsout=tv
  <P>
  	... subtract stars from the peak input image
  <P>
  	... the output images is ypix.sub.3
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  datapars,daopars,nstar,allstar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'OUTPUT' 'ERRORS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>