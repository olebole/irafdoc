group — Group stars based on positional overlap and signal/noise
================================================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>group (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>group (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>group</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  group -- group stars in a photometry file
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  group image photfile psfimage groupfile
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images containing the stars to be grouped.
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
  Photfile is normally the output of the PHOT task but may also be the output of
  the PSF, PEAK, NSTAR and ALLSTAR tasks. Photfile may be an APPHOT/DAOPHOT
  text database or an STSDAS binary table.
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
  <DT><B><A NAME="l_groupfile">groupfile = </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='groupfile' Line='groupfile = '>
  <DD>The list of output grouped photometry files. There must be one output group
  photometry file for every input image.  If groupfile is "<TT>default</TT>",
  "<TT>dir$default</TT>", or a directory specification then GROUP writes a file called
  image.grp.? where ? is the next available version number. If the DAOPHOT
  package parameter <I>text</I> is "<TT>yes</TT>" then an APPHOT/DAOPHOT text database is
  written, otherwise an STSDAS table is written.
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
  <I>groupfile</I>. The image header coordinate system is used to transform from
  the input coordinate system to the "<TT>logical</TT>" system used internally, from the
  internal logical system to the PSF model system, and from the internal
  "<TT>logical</TT>" pixel coordinate system to the output coordinate system. The input
  coordinate system options are "<TT>logical</TT>", "<TT>tv</TT>", "<TT>physical</TT>", and "<TT>world</TT>". The PSF
  model and output coordinate system options are "<TT>logical</TT>", "<TT>tv</TT>", and "<TT>physical</TT>".
  The image cursor coordinate system is assumed to be the "<TT>tv</TT>" system.
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
  <DD>Verify the critical GROUP task parameters? Verify can be set to the DAOPHOT
  package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = "<TT>)_.update</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = ")_.update"'>
  <DD>Update the GROUP task parameters if <I>verify</I> is "<TT>yes</TT>"? Update can be
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
  GROUP takes the photometry file <I>photfile</I> file containing the stellar
  coordinates and photometry and associates the stars into natural groups based
  upon proximity and the magnitude level at which they overlap. The results are
  written into <I>groupfile</I>.  If the DAOPHOT package parameter <I>text</I> is
  "<TT>yes</TT>" then <I>groupfile</I> is a text database, otherwise it is an STSDAS table.
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
  The coordinates written to <I>groupfile</I> are in the coordinate system
  defined by <I>wcsout</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>", and "<TT>physical</TT>". The
  simplest default is the "<TT>logical</TT>" system.  Users wishing to correlate the
  output coordinates of objects measured in image sections or mosaic  pieces
  with coordinates in the parent image must use the "<TT>tv</TT>" or "<TT>physical</TT>"
  coordinate systems.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the input image pixels are cached in memory. If caching
  is enabled and the first data access will appear to take a long time as the
  entire image must be read in before the measurement is actually made. All
  subsequent data requests will be very fast because GROUP is accessing memory
  not disk. The point of caching is to speed up random image access by making
  the internal image i/o buffers the same size as the image itself. There is
  no point in turning caching on unless a lot of the input magnitudes are INDEF.
  In that case GROUP must access the image to estimate a magnitude. Also at
  present there is no point in enabling caching for images that are less than
  or equal to 524288 bytes, i.e. the size of the test image dev$ypix, as the
  default image i/o buffer is exactly that size. However if the size of dev$ypix
  is doubled by converting it to a real image with the chpixtype task then the
  effect of caching in interactive is can be quite noticeable if measurements
  of objects in the top and bottom halves of the image are alternated.
  <P>
  <P>
  The algorithm works in the following manner. If two stars are within a
  distance R pixels of one another, where R = <I>psfrad</I> / <I>scale</I> +
  <I>fitrad</I> / <I>scale</I> + 1, the PSF of the brighter one is evaluated at
  a distance d pixels, where d = <I>fitrad</I> / <I>scale</I> + 1 away from the
  fainter. If this value is larger than <I>critsnratio</I> times the expected
  noise per pixel then the two stars are put into the same group since the
  brighter star is capable of affecting the photometry of the fainter.
  <I>Psfrad</I>, <I>fitrad</I> and <I>critsnratio</I> are the psf radius, the
  fitting radius, and the critical S/N ratio respectively and are located
  in the DAOPARS task. <I>Scale</I> is the image scale parameter and is located
  in the DATAPARS task. In order for this algorithm to work correctly it is
  imperative that the DATAPARS readnoise and gain parameters <I>readnoise</I>
  and <I>gain</I> be set correctly as these values are used to compute the
  expected random noise per pixel.
  <P>
  The correct value of <I>critsnratio</I> must be determined by trial and error.
  For example if a critical S/N ratio of 0.1 divides all the stars in the image
  into groups smaller than the <I>maxgroup</I> parameter in the DAOPARS task, then
  unavoidable random errors will dominate over crowding errors.  If a critical
  S/N ratio of 1.0 works, then crowding errors will be no worse than the random
  errors. If a critical S/N ratio much greater than 1 is required then in most
  cases crowding will be the dominant source or error.
  <P>
  If <I>verbose</I> is set to "<TT>yes</TT>", GROUP will write a table on the terminal
  showing the number of groups as a function of group size. If any group is
  larger than <I>maxgroup</I> then <I>critnsratio</I> must be increased or
  the GRPSELECT task used to cut large groups out of the file. When crowding
  conditions vary across the frame,  GROUP and GRPSELECT can be used together
  to get the best possible photometry for stars in different crowding regimes.
  <P>
  If any stars in <I>photfile</I> have INDEF magnitudes, GROUP will attempt
  to estimate a magnitude for them based on the weighted sum of the pixels
  of a radial weighting function and the value of the PSF at that point.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Group the PHOT task output results for the test image dev$ypix using
  a critical S/N ratio of 1 and printing the output summary on the terminal.
  Good stars for making the PSF model can be found at (442,410), (348,189),
  and (379,67).
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
  <P>
      da&gt; group dev$ypix default default default crit=1.0 verbose+
  <P>
          ... verify the critical parameters
  <P>
          ... answers will appear in ypix.grp.1
  <P>
  </PRE>
  <P>
  <P>
  2. Run group on a section of the input image using the photometry file and PSF
  model derived in example 1 for the parent image and writing the results
  in the coordinate system of the parent image. Note that the results for
  example 2 are identical to those in example 1.
  <P>
  <PRE>
      da&gt; group dev$ypix[150:450,150:450] default default default  \<BR>
          wcsin=tv wcspsf=tv wcsout=tv
  <P>
          ... answer the verify prompts
  <P>
          ... fit the stars
  <P>
          ... the results will appear in ypix.grp.2
  <P>
      da&gt; display dev$ypix[150:450,150:450] 1
  <P>
          ... display the image
  <P>
      da&gt; pdump ypix.grp.2 xc,yc yes | tvmark 1 STDIN col=204
  <P>
          ... mark the stars
  <P>
  </PRE>
  <P>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
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
  psf,grpselect,nstar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>