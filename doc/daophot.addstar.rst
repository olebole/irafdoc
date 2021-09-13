addstar — Add artificial stars to an image using the computed psf
=================================================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>addstar (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>addstar (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>addstar</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  addstar -- add artificial stars to images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  addstar image photfile psfimage addimage
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images to which artificial stars are to be added.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_photfile">photfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photfile' Line='photfile'>
  <DD>The list of photometry files containing the x and y coordinates and magnitudes
  of the artificial stars to be added to <I>image</I>. If photfile is undefined,
  then <I>nstar</I> artificial stars uniformly distributed in position, and  in
  magnitude between <I>minmag</I> and <I>maxmag</I> are added to <I>image</I>. If
  photfile is defined, there must be one photometry file for every input image.
  Photfile may be a simple text file containing x, y, magnitude, and id number in
  columns 1, 2, 3, and 4 respectively (<I>simple_text</I> = yes), an APPHOT/DAOPHOT
  text database file (<I>simple_text</I> = no), or an STSDAS binary table file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_psfimage">psfimage</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='psfimage' Line='psfimage'>
  <DD>The list of images containing the PSF models computed by the DAOPHOT PSF task.
  The number of PSF images must be equal to the number of input images. If
  psfimage is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification, then PEAK
  will look for an image with the name image.psf.?, where ? is the highest
  existing version number.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_addimage">addimage</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='addimage' Line='addimage'>
  <DD>The root name of the output images. There must be one output root image name
   for every input image. If addimage is "<TT>default</TT>", "<TT>dir$default</TT>" or a directory
  specification, then an output artificial image and artificial star list called
  image.add.? and image.art.? respectively are created, where ? is the next
  available version number. If the DAOPHOT  package parameter <I>text</I> is "<TT>yes</TT>",
  then an APPHOT/DAOPHOT text database file is written, otherwise an STSDAS binary
  table is written.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_minmag">minmag</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minmag' Line='minmag'>
  <DD>The minimum magnitude of the computer generated artificial stars to be
  added to the image. The actual intensities of the pixels in the artificial
  stars are computed with respect to the magnitude of the PSF stored in
  <I>psfimage</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_maxmag">maxmag</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxmag' Line='maxmag'>
  <DD>The maximum magnitude of the computer generated artificial stars to be
  added to the image. The actual intensities of the pixels in the artificial
  stars are computed with respect to the magnitude of the PSF stored in
  <I>psfimage</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nstar">nstar</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nstar' Line='nstar'>
  <DD>The number of computer generated artificial stars to be added to the input
  image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_datapars">datapars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""'>
  <DD>The text file in which the data dependent parameters are stored. The gain
  parameter <I>epadu</I> in electrons per ADU is stored here.  If datapars is
  undefined then the default parameter set in the user's uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_daopars">daopars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='daopars' Line='daopars = ""'>
  <DD>The text file in which the daophot fitting parameters are stored. The PSF
  radius parameter <I>psfrad</I> in scale units is stored here. If daopars is
  undefined then the default parameter set in the user's uparm directory is used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_simple_text">simple_text = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='simple_text' Line='simple_text = no'>
  <DD>If <I>photfile</I> is a text file and <I>simple_text</I> = "<TT>no</TT>", then ADDSTAR
  expects an APPHOT/DAOPHOT database. Otherwise ADDSTAR expects a simple list
  format with x, y, magnitude, and id in columns 1, 2,3, and 4 respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_seed">seed = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='seed' Line='seed = 0'>
  <DD>The seed for the random number generator used to generate the positions
  and magnitudes of the artificial stars.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nimage">nimage = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nimage' Line='nimage = 1'>
  <DD>The number of output images to be created per input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_idoffset">idoffset = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='idoffset' Line='idoffset = 0'>
  <DD>The integer offset to be added to the id numbers of stars in the output
  artificial photometry file. By default the artificial stars are numbered from 1
  to N where N is the number of artificial stars added to the input frame.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcsin">wcsin = "<TT>)_.wcsin</TT>", wcsout = "<TT>)_.wcsout</TT>", wcspsf = "<TT>)_.wcspsf</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsin' Line='wcsin = ")_.wcsin", wcsout = ")_.wcsout", wcspsf = ")_.wcspsf"'>
  <DD>The coordinate system of the input coordinates read from <I>photfile</I>, of the
  psf model <I>psfimage</I>, and of the output coordinates written to
  <I>addimage</I> respectively. The image header coordinate system is used to
  transform from the input coordinate system to the "<TT>logical</TT>" pixel coordinate
  system used internally, from the internal logical system to the PSF model
  system, and from the internal "<TT>logical</TT>" pixel coordinate system to the output
  coordinate system. The input coordinate system options are "<TT>logical</TT>", "<TT>tv</TT>",
  "<TT>physical</TT>", and "<TT>world</TT>". The PSF model and output coordinate system options
  are "<TT>logical</TT>", "<TT>tv</TT>", and "<TT>physical</TT>". The image cursor coordinate system is
  assumed to be the "<TT>tv</TT>" system.
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
  <DD>Verify the critical ADDSTAR task parameters? Verify may be set to the
  daophot package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = "<TT>)_.update</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = ")_.update"'>
  <DD>Update the critical ADDSTAR task parameters if <I>verify</I> = "<TT>yes</TT>"?
  Update may be set to the daophot package parameter value (the default),
  "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = "<TT>)_.verbose</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages about the progress of ADDSTAR? Verbose may be set to the
  daophot package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  ADDSTAR adds artificial stars, whose positions and magnitudes are listed in
  <I>photfile</I> or generated at random by the computer, to the input image
  <I>image</I> using the PSF in <I>psfimage</I>, and writes the result to the
  output image and output photometry file <I>addimage</I>. If <I>photfile</I> is
  undefined then ADDSTAR generates an artificial photometry list containing
  <I>nstar</I> stars uniformly distributed in position over the image and in
  magnitude between <I>minmag</I> and <I>maxmag</I>. The input photometry file
  may be an STSDAS binary table or an APPHOT/DAOPHOT text database file (the
  output of the PHOT, PSF, PEAK, NSTAR, or ALLSTAR tasks) or a simple text file
  with the x and y positions, magnitude, and id in columns 1, 2, 3 and 4
  respectively. The ids of stars in the output photometry file may be set to
  numbers outside the range of the real data by setting the parameter
  <I>offset</I>. Several output images may be written for each input image by
  setting the parameter <I>nimage</I> greater than 1.
  <P>
  The coordinates read from <I>photfile</I> are assumed to be in coordinate
  system defined by <I>wcsin</I>. If photfile is undefined the input coordinate
  system is logical. The options are "<TT>logical</TT>", "<TT>tv</TT>", "<TT>physical</TT>", and "<TT>world</TT>"
  and the transformation from the input coordinate system to the internal
  "<TT>logical</TT>" system is defined by the image coordinate system. The simplest
  default is the "<TT>logical</TT>" pixel system. Users working on with image sections but
   importing pixel coordinate lists generated from the parent image must use the
  "<TT>tv</TT>" or "<TT>physical</TT>" input coordinate systems.
  <P>
  The coordinate system of the PSF model is the coordinate system defined by the
  <I>wcspsf</I> parameter. Normally the PSF model was derived from the input image
  and this parameter default to "<TT>logical</TT>". However if the PSF model was derived
  from a larger image which is a "<TT>parent</TT>" of the input image, then wcspsf should
  be set to "<TT>tv</TT>" or "<TT>physical</TT>" depending on the circumstances.
  <P>
  The coordinates written to <I>addimage</I> are in the coordinate system defined
  by <I>wcsout</I>.  The options are "<TT>logical</TT>", "<TT>tv</TT>", and "<TT>physical</TT>". The simplest
  default is the "<TT>logical</TT>" system.  Users wishing to correlate the output
  coordinates of objects measured in image sections or mosaic pieces with
  coordinates in the parent image must use the "<TT>tv</TT>" or "<TT>physical</TT>" coordinate
  systems.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the output image pixels are cached in memory. If caching
  is enabled and the first artificial star addition will appear
  to take a long time as the entire input image must be read into the output
  image before the first artificial star addition is actually made. All
  subsequent measurements will be very fast because ADDSTAR is accessing memory
  not disk. The point of caching is to speed up random image access by making
  the internal image i/o buffers the same size as the image itself. However if
  the input object lists are sorted in row order and sparse caching may actually
  worsen not improve the execution time. Also at present there is no point in
  enabling caching for images that are less than or equal to 524288 bytes, i.e.
  the size of the test image dev$ypix, as the default image i/o buffer is exactly
  that size. However if the size of dev$ypix is doubled by converting it to a
  real image with the chpixtype task then the effect of caching in interactive
  is can be quite noticeable if measurements of objects in the top and bottom
  halves of the image are alternated.
  <P>
  The intensities in the artificial stellar images are computed relative to the
  intensities in the PSF image, by scaling the magnitudes of the artificial stars
  to the magnitude of the PSF in <I>psfimage</I>. Poisson noise is added to the
  artificial stars using the value of the gain stored in the image header keyword
  specified by the DATAPARS parameter <I>gain</I> if present, or the value of the
  DATAPARS parameter <I>epadu</I>.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_output">OUTPUT</A></H2>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  If <I>verbose</I> = yes, a line of output is written to the terminal for each
  artificial star added to the input image.
  <P>
  Full output is written to the output photometry file <I>addimage</I>. At the
  beginning of each file is a header listing the current values of all the
  parameters. For each artificial star added to the input image the following
  record is written.
  <P>
  <PRE>
  	id  xcenter  ycenter  mag
  </PRE>
  <P>
  Id is the id number of the star, xcenter and ycenter are its coordinates, and
  mag is its magnitude.
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Add 30 stars uniformly distributed between 17 and 20th magnitude and in
  position to the input image m92. Display the new image and mark the
  artificial stars. Good stars for making the PSF model can be found at
  (442,410), (348,189), and (379,67).
  <P>
  <PRE>
      da&gt; daofind dev$ypix default fwhmpsf=2.5 sigma=5.0 threshold=20.0
  <P>
          ... answer verify prompts
  <P>
          ... find stars in the image
  <P>
          ... answer will appear in ypix.coo.1
  <P>
      da&gt; phot dev$ypix default default annulus=10. dannulus=5.       \<BR>
          apertures = 5.0
  <P>
          ... answer verify prompts
  <P>
          ... do aperture photometry on the detected stars
  <P>
          ... answer will appear in ypix.mag.1
  <P>
      da&gt; display dev$ypix 1
  <P>
  	... display the image
  <P>
      da&gt; psf dev$ypix default "" default default default psfrad=9.0 \<BR>
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
      da&gt; addstar dev$ypix "" default default 12.0 17.0 30 epadu=14.0
  <P>
  	... verify the critical parameters
  <P>
      da&gt; display ypix.add.1 2
  <P>
  	... display the artificial image
  <P>
      da&gt; pdump ypix.art.1 xcenter,ycenter yes | tvmark 2 STDIN col=204
  <P>
  	... mark the stars on the artificial image
  </PRE>
  <P>
  <P>
  2. Repeat example 1 using the output starlist as input.
  <P>
  <PRE>
      da&gt; addstar dev$ypix ypix.art.1  default default simple- epadu=14.0
  <P>
      ... the answers will appear in ypix.add.2 and ypix.art.2
  </PRE>
  <P>
  <P>
  3. Repeat example 1 using a simple text file as input.
  <P>
  <PRE>
      da&gt; pdump ypix.art.1 xc,yc,mag yes &gt; artdata
  <P>
      ... create a simple text file from the addstar output
  <P>
      da&gt; addstar dev$ypix artdata default default simple+ epadu=14.0
  <P>
      ... the answers will appear in ypix.add.3 and ypix.art.3
  </PRE>
  <P>
  <P>
  4. Run addstar on a section of the input image using the PSF model derived in
  example 1 for the parent image, the artificial star list from examples 2 and
  3, and write the results in the coordinate system of the image section
  not the parent image.
  <P>
  <PRE>
     da&gt; addstar dev$ypix[150:450,150:450] artdata default default simple+ \<BR>
         epadu=14.0 wcsin=tv wcspsf=tv wcsout=logical
  <P>
          ... answer the verify prompts
  <P>
          ... fit the stars
  <P>
          ... the results will appear in ypix.add.4 and ypix.art.4
  <P>
      da&gt; display ypix.add.4 1
  <P>
          ... display the image
  <P>
      da&gt; pdump ypix.art.4 xc,yc yes | tvmark 1 STDIN col=204
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
  datapars,daopars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'OUTPUT' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>