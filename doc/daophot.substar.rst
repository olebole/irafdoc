.. _substar:

substar — Subtract the fitted stars from the original image
===========================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  substar -- subtract photometry results from an image 
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  substar image photfile exfile psfimage subimage
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images from which to subtract the scaled and shifted PSF.
  </DD>
  </DL>
  <DL>
  <DT><B>photfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photfile' Line='photfile'>
  <DD>The list of PSF fitted photometry files. There must be one photometry file
  for every input image. If photfile is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory
  specification, SUBSTAR will look for a file called image.nst.? where the
  question mark stands for the highest existing version number. Photfile is
  usually the output of the NSTAR task but may also be the output of the PEAK
  and ALLSTAR tasks or even the PHOT task. Photfile may be an APPHOT/DAOPHOT text
  database or an STSDAS table.
  </DD>
  </DL>
  <DL>
  <DT><B>exfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='exfile' Line='exfile'>
  <DD>The list of photometry files containing the ids of stars to be excluded
  from the subtraction. Exfile must be undefined or contain one exclude file
  for every input image. If exfile is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory
  specification, SUBSTAR will look for a file called image.pst.? where the ?
  mark stands for the highest existing version number. Exfile is usually the
  output of the PSTSELECT task but may also be the output of the PEAK, NSTAR and
  ALLSTAR tasks or even the PHOT task. Exfile may be an APPHOT/DAOPHOT text
  database or an STSDAS table.
  </DD>
  </DL>
  <DL>
  <DT><B>psfimage</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='psfimage' Line='psfimage'>
  <DD>The list of images containing the PSF models computed by the DAOPHOT PSF task.
  The number of PSF images must be equal to the number of input images.  If
  psfimage is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification,
  then PEAK will look for an image with the name image.psf.?, where
  ? is the highest existing version number.
  </DD>
  </DL>
  <DL>
  <DT><B>subimage</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='subimage' Line='subimage'>
  <DD>The list of output subtracted images. There must be one output subtracted
  image for every input image.  If subimage is "<TT>default</TT>", "<TT>dir$default</TT>", or a
  directory specification, then SUBSTAR will write an image called image.sub.?
  where question mark stands for the next available version number. 
  </DD>
  </DL>
  <DL>
  <DT><B>datapars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""'>
  <DD>The name of the file containing the data dependent parameters. The parameters
  <I>scale</I>, <I>datamin</I>, and <I>datamax</I> are located here. If datapars
  is undefined then the default parameter set in uparm directory
  </DD>
  </DL>
  <DL>
  <DT><B>daopars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='daopars' Line='daopars = ""'>
  <DD>The name of the file containing the daophot fitting parameters. The parameters
  <I>psfrad</I> and <I>fitrad</I> are located here. If <I>daopars</I> is undefined
  then the default parameter set in uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B>wcsin = "<TT>)_.wcsin</TT>", wcsout = "<TT>)_.wcsout</TT>", wcspsf = "<TT>)_.wcspsf</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsin' Line='wcsin = ")_.wcsin", wcsout = ")_.wcsout", wcspsf = ")_.wcspsf"'>
  <DD>The coordinate system of the input coordinates read from <I>photfile</I>, of the
  psf model <I>psfimage</I>, and of the output coordinates written to
  the standard output if <I>verbose</I> = "<TT>yes</TT>". The image header coordinate
  system is used to transform from the input coordinate system to the "<TT>logical</TT>"
  pixel coordinate system used internally, from the internal logical system to
  the PSF model system, and from the internal "<TT>logical</TT>" pixel coordinate system
  to the output coordinate system. The input coordinate system options are
  "<TT>logical</TT>", "<TT>tv</TT>", "<TT>physical</TT>", and "<TT>world</TT>". The PSF model and output coordinate
  system options are "<TT>logical</TT>", "<TT>tv</TT>", and "<TT>physical</TT>". The image cursor coordinate
  system is assumed to be the "<TT>tv</TT>" system.
  <DL>
  <DT><B>logical</B></DT>
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
  <DT><B>tv</B></DT>
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
  <DT><B>physical</B></DT>
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
  <DT><B>world</B></DT>
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
  <DT><B>cache = "<TT>)_.cache</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = ")_.cache"'>
  <DD>Cache the image pixels in memory. Cache may be set to the value of the apphot
  package parameter (the default), "<TT>yes</TT>", or "<TT>no</TT>". By default caching is
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B>verify = "<TT>)_.verify</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = ")_.verify"'>
  <DD>Verify the critical SUBSTAR task parameters? Verify can be set to the DAOPHOT
  package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>update = "<TT>)_update</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = ")_update"'>
  <DD>Update the SUBSTAR task parameters if <I>verify</I> is "<TT>yes</TT>"? Update can be
  set to the default daophot package parameter value, "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = "<TT>)_.verbose</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages about the progress of the task ? Verbose can be set to the
  DAOPHOT package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  SUBSTAR task takes an input photometry list <I>photfile</I> containing
  the fitted coordinates and magnitudes, and an input PSF <I>psfimage</I>, and
  for each star in the photometry list scales and shifts the PSF and subtracts
  it from the input image <I>image</I>. The final subtracted image is saved in the
  output image <I>subimage</I>.
  <P>
  The input photometry list can be the output from of the PEAK, NSTAR or ALLSTAR
  tasks or even the PHOT task although most people would not want to use the PHOT
  output for this purpose.
  <P>
  Selected stars may be omitted from the subtraction by supplying their ids in
  the file <I>exfile</I>. <I>Exfile</I> is normally the output the PSTSELECT task
  and is used to tell SUBSTAR to subtract the PSF star neighbors, but not the
  PSF stars themselves.
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
  The coordinates written to the standard output if <I>verbose</I> = yes are in the
  coordinate system defined by <I>wcsout</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>",
  and "<TT>physical</TT>". The simplest default is the "<TT>logical</TT>" system. Users wishing to
  correlate the output coordinates of objects measured in image sections or
  mosaic pieces with coordinates in the parent image must use the "<TT>tv</TT>" or
  "<TT>physical</TT>" coordinate systems.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough the input and output image pixels are cached in memory. If
  caching is enabled and SUBSTAR is run interactively the first subtraction
  will appear to take a long time as the entire image must be read in before
  the measurement is actually made. All subsequent measurements will be very
  fast because SUBSTAR is accessing memory not disk. The point of caching is
  to speed up random image access by making the internal image i/o buffers the
  same size as the image itself. However if the input object lists are sorted
  in row order which SUBSTAR does internally  and are sparse caching may
  actually worsen not improve the execution time. Also at present there is no
  point in enabling caching for images that are less than or equal to 524288
  bytes, i.e. the size of the test image dev$ypix, as the default image i/o
  buffer is exactly that size. However if the size of dev$ypix is doubled by
  converting it to a real image with the chpixtype task then the effect of
  caching in interactive is can be quite noticeable if measurements
  of objects in the top and bottom halves of the image are alternated.
  <P>
  <P>
  The SUBSTAR task is most commonly used to check on the quality of the PSF
  fitting produced by PEAK and NSTAR, to search for non-stellar objects and close
  binary stars, to generate an improved PSF in crowded fields, and to remove
  neighbors from bright stars which are to be used to determine aperture
  corrections.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Subtract the NSTAR photometry results for the test image dev$ypix from the
  image dev$ypix.
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
      da&gt; group dev$ypix default default default
  <P>
          ... verify the prompts
  <P>
          ... the output will appear in ypix.grp.1
  <P>
      da&gt; nstar dev$ypix default default default default
  <P>
          ... verify the prompts
  <P>
          ... the results will appear in ypix.nst.1 and ypix.nrj.1
  <P>
      da&gt; pdump ypix.nst.1 sharpness,chi yes | graph
  <P>
          ... plot chi versus sharpness, the stars should cluster around
              sharpness = 0.0 and chi = 1.0, note that the frame does
              not have a lot of stars
  <P>
      da&gt; substar dev$ypix default  "" default default
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
  2. Rerun the previous example on a section of the test image  using the group
  file and PSF model derived in example 1 for the parent image and writing the
  results in the coordinate system of the parent image.
  <P>
  <PRE>
      da&gt; nstar dev$ypix[150:450,150:450] default default default default \<BR>
          wcsin=tv wcspsf=tv wcsout=tv
  <P>
          ... answer the verify prompts
  <P>
          ... fit the stars
  <P>
          ... the results will appear in ypix.nst.2 and ypix.nst.2
  <P>
      da&gt; display dev$ypix[150:450,150:450] 1
  <P>
          ... display the image
  <P>
      da&gt; pdump ypix.nst.2 xc,yc yes | tvmark 1 STDIN col=204
  <P>
          ... mark the stars
  <P>
      da&gt; substar dev$ypix ypix.nst.2 "" default default
  <P>
          ... subtract stars from parent image
  <P>
          ... the output images is ypix.sub.2
  <P>
  <P>
      da&gt; substar dev$ypix[150:450,150:450] ypix.nst.2 "" default default  \<BR>
          wcsin=tv wcspsf=tv wcsout=tv
  <P>
          ... subtract stars from the nstarinput image
  <P>
          ... the output images is ypix.sub.3
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  datapars,daopars,nstar,peak
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
