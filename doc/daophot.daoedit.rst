.. _daoedit:

daoedit — Review/edit algorithm parameters interactively
========================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  daoedit -- edit the daophot package parameters interactively
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  daoedit image
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD></DD>
  </DL>
  <DL>
  <DT><B>icommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The image display cursor or image cursor commands file.
  </DD>
  </DL>
  <DL>
  <DT><B>gcommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The graphics cursor or graphics cursor commands file.
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
  <DT><B>graphics = "<TT>)_.graphics</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = ")_.graphics"'>
  <DD>The standard graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B>display = "<TT>)_.display</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = ")_.display"'>
  <DD>The standard display device.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  DAOEDIT is a general purpose tool for interactively examining and editing
  the DAOPHOT algorithm parameters located in the parameter sets DATAPARS,
  FINDPARS, CENTERPARS, FITSKYPARS, PHOTPARS, and DAOPARS. These five parameter
  sets can be listed, edited, and/or unlearned as a group from within DAOEDIT
  using the IRAF LPAR, EPAR and UNLEARN utilities.  Any parameter in each of
  these five parameter sets can be examined or edited individual using a simple 
  command.  Parameters which are defined in terms of radial distance from the
  center of a star or in terms of image counts can be examined and edited
  interactively using radial profile plots and the graphics cursor.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the input image pixels are cached in memory. If caching
  is enabled the first data measurement will appear to take a long time as the
  entire image must be read in before the measurement is actually made. All
  subsequent measurements will be very fast because DAOEDIT is accessing memory
  not disk.  The point of caching is to speed up random image access by making
  the internal image i/o buffers the same size as the image itself. At present
  there is no point in enabling caching for images that are less than or equal
  to 524288 bytes, i.e. the size of the test image dev$ypix, as the default image
   i/o buffer is exactly that size. However if the size of dev$ypix is doubled by
   converting it to a real image with the chpixtype task then the effect of
  caching in interactive is can be quite noticeable if measurements of objects
  in the top and bottom halves of the image are alternated.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  <PRE>
  		      Interactive Keystroke Commands
  <P>
  ?	Print help
  :	Colon commands
  a	Estimate center, sky, skysigma, fwhmpsf and magnitude of a star
  r	Plot the radial profile of a star and its integral
  i	Set selected parameters interactively using a radial profile plot
  g	Toggle between image and graphics cursor
  x	Toggle the radial profile plot between pixel and scale units
  y	Toggle the radial profile plot between counts and normal units
  q	Quit task
  <P>
  		      Colon Commands
  <P>
  :lparam/eparam/unlearn	pset	List/edit/unlearn the named pset
  :parameter	        [value]	List or set an individual pset parameter
  <P>
  <P>
  		      Psets
  <P>
  datapars	The data dependent parameters
  findpars	The daofind task object detection parameters
  centerpars	The phot task centering algorithm parameters
  fitskypars	The phot task sky fitting algorithm parameters
  photpars	The phot task photometry algorithm parameters
  daopars		The psf fitting algorithm parameters
  <P>
  <P>
  The following commands are available from within the interactive setup
  menu.
  <P>
  <P>
  	    Interactive Daoedit Setup Menu
  <P>
  ?	Print help
  spbar	Mark/verify critical parameters (f, s, a, d, r, w, b)
  q	Quit
  <P>
  f	Mark/verify the fwhm of the psf on the radial profile plot
  s	Mark/verify the sky sigma on the radial profile plot
  l	Mark/verify the minimum good data value on the radial profile plot
  u	Mark/verify the maximum good data value on the radial profile plot
  <P>
  c	Mark/verify the centering box half-width on the radial profile plot
  n	Mark/verify the cleaning radius on the radial profile plot
  p	Mark/verify the clipping radius on the radial profile plot
  <P>
  a	Mark/verify the inner sky annulus radius on the radial profile plot
  d	Mark/verify the width of the sky annulus on the radial profile plot
  g	Mark/verify the sky region growing radius on the radial profile plot
  <P>
  r	Mark/verify the photometry aperture(s) on the radial profile plot
  w	Mark/verify the psf function radius on the radial profile plot
  b	Mark/verify the psf fitting radius on the radial profile plot
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Setup the daophot package parameters interactively for the image m92.
  This example assumes that the parameters are all initially at their 
  default values.
  <P>
  <PRE>
  	da&gt; display dev$ypix 1
  	da&gt; daoedit dev$ypix
  <P>
  	    ... type :e datapars to edit the data dependent parameters
  	    ...	leave scale at 1.0 and datamin at INDEF but set the
  	        datamax, readnoise, epadu, exposure, airmass, filter,
  		and obstime parameters to appropriate values
  	    ... type :l datapars to check the results of the editing
  <P>
  	    ... type :e findpars to check the object detection parameters
  	    ... change the findpars threshold parameter from 4.0 to 5.0
  		using the command :threshold 5.0
  <P>
  	    ... type i to enter the interactive setup menu
  		set the fwhmpsf, sigma, inner radius of the sky annulus,
  		width of the sky annulus, photometry aperture(s), psf
  		radius, and fitting radius using the radial profile
  		plot and graphics cursor
  <P>
  	    ... select a bright non-saturated star and check that its
  		radial profile is normal using the r keystroke command
  	    ... note the value of the standard deviation of the sky
  	        background written in the plot header
  	    ... set the datapars sigma parameter to this value using
  		the command :sigma &lt;value&gt;
  <P>
  	    ... check the data definition, centering, sky fitting,
  	        photometry, and psf fitting parameters with the commands
  		:l datapars, :l centerpars, :l fitskypars, :l photpars,
  		and :l daopars
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
  datapars,findpars,centerpars,fitskypars,photpars,daopars,setimpars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
