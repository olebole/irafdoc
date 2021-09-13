.. _pstselect:

pstselect — Select candidate psf stars based on proximity
=========================================================

**Package: daophot**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pstselect -- select candidate psf stars from a photometry file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pstselect image photfile pstfile maxnpsf
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of images containing the candidate psf stars.
  </DD>
  </DL>
  <DL>
  <DT><B>photfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photfile' Line='photfile'>
  <DD>The list of input  photometry files. The number of photometry files must
  be equal to the number of input images. If photfile is "<TT>default</TT>", "<TT>dir$default</TT>",
  or a directory specification PSTSELECT searches for a file called 
  dir$image.mag.#  where # is the highest available version number for the file.
  Photfile is normally the output of the PHOT task but may also be the  output
  of  the  PSF,  PEAK,  NSTAR and ALLSTAR tasks. Photfile may be a
  text file or an STSDAS binary table.
  </DD>
  </DL>
  <DL>
  <DT><B>pstfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pstfile' Line='pstfile'>
  <DD>The  list  of  output  psf star photometry files. There must be one output
  psf star photometry file for every input image. If pstfile is "<TT>default</TT>",
  "<TT>dir$default</TT>",  or a  directory  specification  then  PSTSELECT writes
  a file called dir$image.pst.# where # is the next  available  version  number.
  Pstfile  inherits its file type, it may be either an APPHOT/DAOPHOT
  text or STSDAS binary file, from photfile.
  </DD>
  </DL>
  <DL>
  <DT><B>maxnpsf = 25</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxnpsf' Line='maxnpsf = 25'>
  <DD>The maximum number of candidate psf stars to be selected.
  </DD>
  </DL>
  <DL>
  <DT><B>mkstars = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mkstars' Line='mkstars = no'>
  <DD>Mark the selected or deleted psf stars on the image display ?
  </DD>
  </DL>
  <DL>
  <DT><B>plotfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = ""'>
  <DD>The name of the output file containing mesh, contour, or profile plots of the
  selected PSF stars. If plotfile is undefined no plot file is created; otherwise
  a mesh, contour, or profile plot is written to this file for each PSF star
  selected. Plotfile is opened in append mode and may become very large.
  </DD>
  </DL>
  <DL>
  <DT><B>datapars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datapars' Line='datapars = ""'>
  <DD>The name of the file containing the data dependent parameters. The parameter
  <I>scale</I> is located here. If <I>datapars</I> is undefined then the default
  parameter set in uparm directory is used.
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
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Select the psf stars interactively ? If interactive = yes and icommands is
  undefined, PSTSELECT reads in the star list from <I>photfile</I>, sorts the
  stars by magnitude and waits for commands from the user. If interactive = no
  and icommands="<TT></TT>", PSTSELECT selects candidate PSF stars from <I>photfile</I>
  automatically. If icommands is not undefined then interactive is automatically
  set to "<TT>no</TT>", and commands are read from the image cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B>plottype = "<TT>mesh</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plottype' Line='plottype = "mesh"'>
  <DD>The default plot type displayed when a psf star is selected interactively.
  The choices are "<TT>mesh</TT>", "<TT>contour</TT>", or "<TT>radial</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>icommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The image display cursor or image cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B>gcommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The graphics cursor or graphics cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B>wcsin = "<TT>)_.wcsin</TT>", wcsout = "<TT>)_.wcsout</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsin' Line='wcsin = ")_.wcsin", wcsout = ")_.wcsout"'>
  <DD>The coordinate system of the input coordinates read from <I>photfile</I> and
  of the output coordinates written to <I>pstfile</I> respectively. The image
  header coordinate system is used to transform from the input coordinate
  system to the "<TT>logical</TT>" pixel coordinate system used internally,
  and from the internal "<TT>logical</TT>" pixel coordinate system to the output
  coordinate system. The input coordinate system options are "<TT>logical</TT>", "<TT>tv</TT>",
  "<TT>physical</TT>", and "<TT>world</TT>". The output coordinate system options are "<TT>logical</TT>",
  "<TT>tv</TT>", and "<TT>physical</TT>". The image cursor coordinate system is assumed to
  be the "<TT>tv</TT>" system.
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
  <DT><B>tv  </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='tv' Line='tv  '>
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
  The wcsin and wcsout parameters default to the values of the package
  parameters of the same name. The default values of the package parameters
  wcsin and wcsout are "<TT>logical</TT>" and "<TT>logical</TT>" respectively.
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
  <DD>Verify the critical PSTSELECT parameters ?
  Verify can be set to the DAOPHOT package parameter value (the default),
  "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>update = "<TT>)_.update</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = ")_.update"'>
  <DD>Update the algorithm parameters if verify is "<TT>yes</TT>"?
  Update can be set to the DAOPHOT package parameter value (the default),
  "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = "<TT>)_.verbose</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = ")_.verbose"'>
  <DD>Print messages about the progress of the task in non-interactive mode ?
  Verbose can be set to the DAOPHOT package parameter value (the default),
  "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='' Line=' '>
  <DD>graphics = "<TT>)_.graphics</TT>"
  The default graphics device.  Graphics can be set to the default
  daophot package parameter value, "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>display = "<TT>)_.display</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = ")_.display"'>
  <DD>The  default  image  display  device.  Display can be set to the DAOPHOT
  package parameter value (the default), "<TT>yes</TT>", or "<TT>no</TT>". By default graphics
  overlay is disabled.  Setting display to one of "<TT>imdr</TT>", "<TT>imdg</TT>", "<TT>imdb</TT>", or
  "<TT>imdy</TT>" enables graphics overlay with the IMD graphics kernel.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  PSTSELECT reads the input photometry file <I>photfile</I>, extracts the ID,
  XCENTER, YCENTER, MAG, and MSKY fields for up to <I>maxnpsf</I> psf stars,
  and the results to <I>pstfile</I>. <I>Pstfile</I> automatically inherits the
  file format of <I>photfile</I>.
  <P>
  The coordinates read from <I>photfile</I> are assumed to be in coordinate
  system defined by <I>wcsin</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>", "<TT>physical</TT>",
  and "<TT>world</TT>" and the transformation from the input coordinate system to
  the internal "<TT>logical</TT>" system is defined by the image coordinate system.
  The simplest default is the "<TT>logical</TT>" pixel system. Users working on with
  image sections but importing pixel coordinate lists generated from the parent
  image must use the "<TT>tv</TT>" or "<TT>physical</TT>" input coordinate systems.
  <P>
  The coordinates written to <I>pstfile</I> are in the coordinate system defined
  by <I>wcsout</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>", and "<TT>physical</TT>". The simplest
  default is the "<TT>logical</TT>" system. Users wishing to correlate the output
  coordinates of objects measured in image sections or mosaic pieces with
  coordinates in the parent image must use the "<TT>tv</TT>" or "<TT>physical</TT>" coordinate
  systems.
  <P>
  After reading the star list from <I>photfile</I>, PSTSELECT sorts the list in
  order of increasing magnitude, after rejecting any stars that have INDEF
  valued magnitudes, or which lie less than <I>fitrad</I> / <I>scale</I>
  pixels from the edge of the <I>image</I>. From this list the brightest
  <I>maxnpsf</I> stars which have no brighter neighbor stars within (<I>psfrad</I> +
  <I>fitrad</I>) / <I>scale</I> + 1 pixels are selected as candidate psf stars.
  <I>Psfrad</I> and <I>fitrad</I> are the psf radius and fitting radius parameters
  respectively and are stored in the DAOPARS parameter set. <I>Scale</I> is the
  image scale parameter and is located in the DATAPARS parameter set. Plots,
  either mesh, contour or radial profile depending on the value of
  <I>plottype</I>, of the selected stars may be saved in the file <I>plotfile</I>.
  <P>
  If <I>interactive</I> = "<TT>no</TT>", PSTSELECT reads the star list in <I>photfile</I>,
  selects the candidate psf stars as described above, and writes the results to
  <I>pstfile</I> automatically. If interactive = "<TT>yes</TT>", PSTSELECT reads
  the star list, selects the candidate psf stars and waits for further
  instruction from the user. At this point the user can step through the stars
  chosen by PSTSELECT, check their surface, contour, or radial profile plots
  for blemishes, neighbors etc, and accept the good candidates and reject
  the poor ones, or use the image cursor and/or id number to select psf
  stars until a maximum of <I>maxnpsf</I> stars is reached. At any point in
  this process a previously selected psf star can be deleted.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the input image pixels are cached in memory. If caching
  is enabled and PSTSELECT is run interactively the first data access will appear
  to take a long time as the entire image must be read in before the data
  is actually fetched. All subsequent measurements will be very fast because
  PSTSELECT is accessing memory not disk. The point of caching is to speed up
  random image access by making the internal image i/o buffers the same size as
  the image itself. However if the input object lists are sorted in row order and
  sparse caching may actually worsen not improve the execution time. Also at
  present there is no point in enabling caching for images that are less than
  or equal to 524288 bytes, i.e. the size of the test image dev$ypix, as the
  default image i/o buffer is exactly that size. However if the size of dev$ypix
  is doubled by converting it to a real image with the chpixtype task then the
  effect of caching in interactive is can be quite noticeable if measurements
  of objects in the top and bottom halves of the image are alternated.
  <P>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Cursors</H3>
  <! BeginSection: 'CURSORS'>
  <UL>
  <P>
      The  following  cursor  commands are available once the image cursor
      has been activated.
  <P>
  <PRE>
  <P>
  	Keystroke Commands 
  <P>
  ?	Print help
  p	Print photometry for star nearest the cursor
  l	List the current psf stars
  n	Select the next good candidate psf star from the list
  a	Add star nearest cursor to psf star list
  d	Delete psf star nearest cursor from psf star list
  q	Quit task
  <P>
  	Colon Commands
  <P>
  :p [n]	Print photometry for star n
  :a [n]	Add star n to psf star list
  :d [n]	Delete star n from psf star list
  <P>
  The following cursor commands are available once a star has been selected
  and the graphics cursor has been activated.
  <P>
          Interactive Graphics Keystroke Commands
  <P>
  ?       Print help
  p       Print the photometry for this star
  t       Print the plot parameters and data minimum and maximum
  a       Accept star and proceed
  d       Reject star and select another with image cursor
  m       Plot the default mesh plot for this star
  n       Increase vertical angle by 15 degrees (mesh plot only)
  s       Decrease vertical angle by 15 degrees (mesh plot only)
  w       Decrease horizontal angle by 15 degrees (mesh plot only)
  e       Increase horizontal angle by 15 degrees (mesh plot only)
  c       Plot the default contour plot for this star
  r       Plot the radial profile for this star
  <P>
  <P>
          Colon Graphics Commands
  <P>
  :m [val] [val]  Set the mesh plot vertical and horizontal viewing angles
  :v [val]        Set the mesh plot vertical viewing angle
  :h [val]        Set the mesh plot horizontal viewing angle
  :c [val] [val]  Set the contour plot floor and ceiling levels
  :l [value]      Set the contour plot floor level
  :u [value]      Set the contour plot ceiling level
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSORS'>
  <H3>Output</H3>
  <! BeginSection: 'OUTPUT'>
  <UL>
  <P>
  If <I>verbose</I> = "<TT>yes</TT>" a single line is written to the terminal for each
  star added to the candidate psf star list. Full output is written to the
  file <I>pstfile</I>. At the beginning of this file is a header listing the
  values of all the important parameters. For each star included in the candidate
  psf star list the following quantities are written.
  <P>
  <PRE>
  	id  xcenter ycenter mag msky
  </PRE>
  <P>
  Id, xcenter, ycenter, mag, and msky are the id, x and y coordinates,
  magnitudes and sky values for the candidate psf stars listed in
  <I>photfile</I>.
  <P>
  </UL>
  <! EndSection:   'OUTPUT'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Select up to 10 psf stars from the PHOT task output non-interactively. 
  Save surface plots of the selected stars in the file "<TT>psf.plots</TT>".
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
      da&gt; pstselect dev$ypix default default 10 psfrad=9.0 fitrad=3.0 \<BR>
          plotfile=psf.plots
  <P>
          ... answer verify prompts
  <P>
          ... select candidate psf stars
  <P>
          ... the output will appear in ypix.pst.1 
  <P>
      da&gt; display dev$ypix 1
  <P>
          ... display the image
  <P>
      da&gt; pdump ypix.pst.1 xc,yc yes | tvmark 1 STDIN col=204
  <P>
          ... mark the stars
  <P>
      da&gt; gkiextract psf.plots 1 | stdgraph
  <P>
  	... make a surface plot of the first candidate psf star
  </PRE>
  <P>
  <P>
  2. Repeat the previous results for an image section while preserving the
  coordinate system of the original image.
  <P>
  <P>
  <PRE>
      da&gt; daofind dev$ypix[150:450,150:450] default wcsout=tv fwhmpsf=2.5 \<BR>
          sigma=5.0 threshold=20.0
  <P>
  	... answer verify prompts
  <P>
          ... find stars in the image
  <P>
  	... answer will appear in ypix.coo.2
  <P>
      da&gt; phot dev$ypix[150:450,150:450] default default wcsin=tv wcsout=tv \<BR>
          annulus=10.  dannulus=5. apertures = 5.0
  <P>
  	... answer verify prompts
  <P>
          ... do aperture photometry on the detected stars
  <P>
  	... answer will appear in ypix.mag.2
  <P>
      da&gt; pstselect dev$ypix[150:450,150:450] default default 10 wcsin=tv \<BR>
          wcsout=tv psfrad=9.0 fitrad=3.0 plotfile=psf.plots2
  <P>
  	... answer verify prompts
  <P>
          ... select candidate psf stars
  <P>
          ... the output will appear in ypix.pst.2 
  <P>
      da&gt; display dev$ypix[150:450,150:450] 1
  <P>
          ... display the image
  <P>
      da&gt; pdump ypix.pst.2 xc,yc yes | tvmark 1 STDIN col=204
  <P>
          ... mark the stars
  <P>
      da&gt; gkiextract psf.plots2 4 | stdgraph
  <P>
  	... make a surface plot of the 4th candidate psf star
  </PRE>
  <P>
  <P>
  3. Repeat example 1 but run pstselect in interactive mode and do not save the
  plots.
  <P>
  <PRE>
      da&gt; display dev$ypix 1
  <P>
          ... display the image 
  <P>
      da&gt; pstselect dev$ypix ypix.mag.1 default 10 psfrad=9. fitrad=3. \<BR>
          interactive+ mkstars+ display=imdr
  <P>
  	... verify the critical parameters as instructed
  <P>
  	... when the image cursor appears type the n keystroke
  	    command to select the first suitable candidate psf
  	    star, examine its surface plot, and type a or d to
  	    accept or reject the candidate
  <P>
  	... repeat the previous command until 10 psf stars have
      	    been selected, the end of the star list is reached,
  	    or a sufficient number of stars but fewer than maxnpsf
  	    have been selected
  <P>
  	... if fewer than maxnpsf stars are found automatically
  	    add psf stars to the list with the a keystroke command
  <P>
  	... type q to quit
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
  datapars,daopars,phot,psf
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSORS' 'OUTPUT' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
