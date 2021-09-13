psf — Compute the point spread function
=======================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>psf (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>psf (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>psf</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  psf -- build the point spread function for an image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  psf image photfile pstfile psfimage opstfile groupfile
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The images for which the PSF model is to be built.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_photfile">photfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='photfile' Line='photfile'>
  <DD>The list of input photometry files. The number of photometry files must
  be equal to the number of input images. If photfile is "<TT>default</TT>", "<TT>dir$default</TT>",
  or a directory specification  PSF searches for a file called dir$image.mag.# 
  where # is the highest available version number for the file. Photfile is
  normally the output of the PHOT task but may also be the  output of the PSF,
  PEAK, NSTAR and ALLSTAR tasks. Photfile may be an APPHOT/DAOPHOT text database
  or an STSDAS binary table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pstfile">pstfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pstfile' Line='pstfile'>
  <DD>The list of input psf star photometry files. The ids of the psf stars in these
  files must be the same as their ids in <I>photfile</I>. The number of psf
  star files must be zero or equal to the number of input images. If pstfile
  is "<TT>default</TT>", "<TT>dir$default</TT>" or a directory specification, PSF searches for
  a file called image.pst.? where ? is the highest existing version number.
  Pstfile is usually the output of the DAOPHOT PSTSELECT task but may also be
  the appropriately edited output psf file produced by PSF itself, or the output
  of the GROUP, NSTAR, PEAK or ALLSTAR tasks.  Photfile may be an APPHOT/DAOPHOT
  text database or an STSDAS table.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_psfimage">psfimage</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='psfimage' Line='psfimage'>
  <DD>The output PSF model image names or directory. The must be one PSF image name
  for every input image. If psfimage is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory
  specification, then PSF creates an image called image.psf.? where ? is the next
  available version number.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_opstfile">opstfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='opstfile' Line='opstfile'>
  <DD>The output psf star files containing lists of the stars actually used to
  compute the PSF model. There must be one output psf star file for every input
  image. If opstfile is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory specification
  then PSF creates a file called image.pst.? where ? is the next available
  version number. If the DAOPHOT package parameter <I>text</I> is "<TT>yes</TT>" then an
  APPHOT/DAOPHOT text database is written, otherwise an STSDAS binary table is
  written.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_groupfile">groupfile</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='groupfile' Line='groupfile'>
  <DD>The output psf star group files listing the PSF stars and their neighbors that
  were used to create the PSF models. There must be one output group file for
  every input image. If groupfile is "<TT>default</TT>", "<TT>dir$default</TT>", or a directory
  specification then PSF creates a file called image.psg.? where ? is the
  next available version number. If the DAOPHOT package parameter <I>text</I> is
  "<TT>yes</TT>" then an APPHOT/DAOPHOT text database is written, otherwise an STSDAS
  table database is written.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plotfile">plotfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = ""'>
  <DD>The name of the output file containing mesh, contour, or profile plots of the
  selected PSF stars. If plotfile is undefined no plot file is created,
  otherwise a mesh, contour, or profile plot is written to this file for each PSF
  star selected. Plotfile is opened in append mode and may become very large.
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
  <DT><B><A NAME="l_matchbyid">matchbyid = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='matchbyid' Line='matchbyid = yes'>
  <DD>Match the stars in the psf star list(s) if any to the stars in the input
  photometry files using id numbers (matchbyid = yes) or x and y positions
  (matchbyid = no).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interactive">interactive = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = yes'>
  <DD>Fit the PSF interactively ? If interactive = yes and <I>icommands</I> is
  undefined, PSF reads selects the initial list of PSF stars from <I>pstfile</I>
  and waits for commands from the user. If interactive = no and <I>icommands</I>
  is undefined, PSF reads in the candidate PSF stars from <I>pstfile</I>, computes
   the PSF, and writes it to <I>psfimage</I> without input from the user. If
  <I>icommands</I> is defined, then interactive = no, and commands are read from
  the image cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mkstars">mkstars = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mkstars' Line='mkstars = no'>
  <DD>Mark the selected or deleted psf stars on the image display ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_showplots">showplots = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='showplots' Line='showplots = yes'>
  <DD>Show plots of the selected PSF stars? After each star is selected
  interactively by the user, a mesh, contour, or profile plot of the data
  subraster around the candidate star is displayed. At this point the user
  can accept or reject the star. In interactive mode the user can set showplots
  to "<TT>yes</TT>" or "<TT>no</TT>".  In non-interactive mode showplots is always "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_plottype">plottype = "<TT>mesh</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plottype' Line='plottype = "mesh"'>
  <DD>The default type of plot displayed when selecting PSF stars. The choices
  are "<TT>mesh</TT>", "<TT>contour</TT>", or "<TT>radial</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_icommands">icommands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The image display cursor or the name of the image cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gcommands">gcommands = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The graphics cursor or the name of the graphics cursor command file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wcsin">wcsin = "<TT>)_.wcsin</TT>", wcsout = "<TT>)_.wcsout</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='wcsin' Line='wcsin = ")_.wcsin", wcsout = ")_.wcsout"'>
  <DD>The coordinate system of the input coordinates read from <I>photfile</I> and
  <I>pstfile</I>, and of the output coordinates written to <I>psfimage</I>,
  <I>opstfile</I>, <I>groupfile</I> respectively. The image header coordinate
  system is used to transform from the input coordinate system to the "<TT>logical</TT>"
  pixel coordinate system used internally, and from the internal "<TT>logical</TT>" pixel
  coordinate system to the output coordinate system. The input coordinate system
  options are "<TT>logical</TT>", tv"<TT>, </TT>"physical"<TT>, and </TT>"world"<TT>. The output coordinate
  system options are </TT>"logical"<TT>, </TT>"tv"<TT>, and </TT>"physical"<TT>. The image cursor coordinate
  system is assumed to be the </TT>"tv"<TT> system.
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
  The wcsin and wcsout parameters default to the values of the package
  parameters of the same name. The default values of the package parameters
  wcsin and wcsout are </TT>"logical"<TT> and </TT>"logical"<TT> respectively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cache">cache = </TT>")_.cache"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cache' Line='cache = ")_.cache"'>
  <DD>Cache the image pixels in memory. Cache may be set to the value of the apphot
  package parameter (the default), </TT>"yes"<TT>, or </TT>"no"<TT>. By default caching is
  disabled.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verify">verify = </TT>")_.verify"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = ")_.verify"'>
  <DD>Verify the critical PSF task parameters? Verify can be set to the DAOPHOT
  package parameter value (the default), </TT>"yes"<TT>, or </TT>"no"<TT>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = </TT>")_.update"<TT></A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = ")_.update"'>
  <DD>Update the PSF task parameters if <I>verify</I> is "<TT>yes</TT>"? Update can be
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
  <DL>
  <DT><B><A NAME="l_graphics">graphics = "<TT>)_.graphics</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = ")_.graphics"'>
  <DD>The default graphics device. Graphics can be set to the default DAOPHOT package
  parameter value, "<TT>yes</TT>", or "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_display">display = "<TT>)_.display</TT>"</A></B></DT>
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
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  The PSF task builds the point spread function for the IRAF image <I>image</I>
  using stars selected, from the input photometry file <I>photfile</I> with the
  image cursor, and/or by their ids stored in the psf star file <I>pstfile</I>,
  and writes the PSF model out to the IRAF image <I>psfimage</I>, the final
  PSF star list to <I>opstfile</I>, and group membership information for the
  selected PSF stars to <I>groupfile</I>. If the DAOPHOT package parameter
  <I>text</I> is "<TT>yes</TT>", then <I>groupfile</I> is an APPHOT/DAOPHOT text database,
  otherwise it is an STSDAS binary table.
  <P>
  The coordinates read from <I>photfile</I> and <I>pstfile</I> are assumed to be
  in coordinate system defined by <I>wcsin</I>. The options are "<TT>logical</TT>", "<TT>tv</TT>",
  "<TT>physical</TT>", and "<TT>world</TT>" and the transformation from the input coordinate
  system to the internal "<TT>logical</TT>" system is defined by the image coordinate
  system. The simplest default is the "<TT>logical</TT>" pixel system. Users working on
  with image sections but importing pixel coordinate lists generated from the
  parent image must use the "<TT>tv</TT>" or "<TT>physical</TT>" input coordinate systems.
  <P>
  The coordinates written to <I>psfimage</I>, <I>pstfile</I> and <I>groupfile</I>
  are in the coordinate system defined by <I>wcsout</I> with the exception
  of the psf model center coordinates PSFX and PSFY which are always in the
  logical system of the input image. The options are "<TT>logical</TT>", "<TT>tv</TT>", and
  "<TT>physical</TT>". The simplest default is the "<TT>logical</TT>" system.  Users wishing to
  correlate the output coordinates of objects measured in image sections or
  mosaic pieces with coordinates in the parent image must use the "<TT>tv</TT>"
  or "<TT>physical</TT>" coordinate systems.
  <P>
  Suitable PSF stars are normally selected interactively using the image display
  and image cursor and matched with the stars in <I>photfile</I> using the cursor
  position and a tolerance specified by the <I>matchrad</I> parameter in the
  DAOPARS task. A star must be in the photometry file before it can be used as
  a PSF star. If a match is found, PSF checks that the candidate star is not too
  close to the edge of the image and that it contains no bad pixels as defined
  by <I>datamin</I> and <I>datamax</I> in the DATAPARS task. After selection a
  mesh, contour, or profile plot of the data subraster around the candidate star
  is displayed in the graphics window, PSF enters graphics cursor command mode
  and the user is given the option to accept or reject the star.  If the user
  accepts the star it is added to the PSF star list.  Commands in the graphics
  cursor menu permit the user to manipulate the floor and ceiling levels of the
  contour plot and the viewing angles for the mesh plot interactively.
  <P>
  Users who know which stars they wish to use as PSF stars ahead of time or
  who are without access to an image display can also select PSF stars by id
  number, after which mesh, contour, or radial profile plots will be displayed in
  the graphics window in the usual way.
  <P>
  If the user does not wish to see any plots of the PSF stars or interact with
  the fitting process, the image cursor may be redirected to a text
  file containing cursor commands <I>icommands</I> which specify the PSF stars
  to be used in the fit. If <I>plotfile</I> is defined contour, mesh, or profile
  plots of the selected psf stars can be saved in a metacode plot file for later
  examination.
  <P>
  In interactive mode the PSF star may be initialized by setting <I>pstfile</I>
  to a file created by the PSTSELECT task. If <I>showplot</I> = "<TT>yes</TT>" the user is
  asked to accept or delete each star in the input psf star list.  Other stars
  may also be added or deleted from this list at any time with the image cursor.
  If <I>interactive</I>=no or <I>icommands</I> is defined, the PSF stars are read
  in from <I>pstfile</I>, and the PSF model is computed and saved without
  input from the user.
  <P>
  If <I>cache</I> is yes and the host machine physical memory and working set size
  are large enough, the input image pixels are cached in memory. If caching
  is enabled and PSF is run interactively the first data access will appear
  to take a long time as the entire image must be read in before the data
  is actually read. All subsequent measurements will be very fast because PSF
  is accessing memory not disk. The point of caching is to speed up random
  image access by making the internal image i/o buffers the same size as the
  image itself. However if the input object lists are sorted in row order and
  sparse caching may actually worsen not improve the execution time. Also at
  present there is no point in enabling caching for images that are less than
  or equal to 524288 bytes, i.e. the size of the test image dev$ypix, as the
  default image i/o buffer is exactly that size. However if the size of dev$ypix
  is doubled by converting it to a real image with the chpixtype task then the
  effect of caching in interactive is can be quite noticeable if measurements
  of objects in the top and bottom halves of the image are alternated.
  <P>
  The output PSF image <I>psfimage</I>  is normally a 2D  image containing the
  image header parameters, "<TT>XPSF</TT>", "<TT>YPSF</TT>", "<TT>PSFMAG</TT>" and "<TT>PSFRAD</TT>" which define the
  centroid, magnitude and size of the PSF model, the parameters "<TT>FUNCTION</TT>",
  "<TT>PSFHEIGH</TT>", "<TT>NPARS</TT>", and "<TT>PAR#</TT>" which define the analytic component of the PSF,
  and a single look-up table of residuals from the analytic fit subsampled by a
  factor of 2 with respect to the parent image.
  <P>
  If the DAOPARS parameter <I>varorder</I> = -1, the PSF is fit by the analytic
  function and <I>psfimage</I> has no pixel file.
  <P>
  If the DAOPARS parameter <I>varorder</I> = 1 or 2, then two or five additional
  lookup tables are computed and <I>psfimage</I> is a 3D image with 3 or 6 planes
  respectively. The first two additional look-up tables contain the first
  derivatives of the PSF wrt the x and y positions in the image (varorder = 1),
  and the next three contains the second derivatives with respect to x ** 2, xy,
  and y ** 2 (varorder = 2).
  <P>
  The positions and magnitudes of each of the stars contributing to the PSF model
  are also stored in the PSF image header.
  <P>
  <I>Groupfile</I> contains a list of the PSF stars, their nearest neighbors, and
  friends of the neighbors. A neighbor is defined to be any star within a
  distance of 1.5 * <I>psfrad</I> / <I>scale</I> + 2.0 * <I>fitrad</I> /
  <I>scale</I> + 1 pixels of the PSF star. Friends of the neighbors are defined
  to be any stars within 2.0 * <I>fitrad</I> / <I>scale</I> + 1.0 of a neighbor
  star. <I>Fitrad</I> and <I>psfrad</I> are respectively the fitting radius and psf
  radius parameters in the DAOPARS task. <I>Scale</I> is the scale factor defined
  in the DATAPARS task.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_cursor_commands">CURSOR COMMANDS</A></H2>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  The following cursor commands are available once the image cursor has
  been activated.
  <P>
  <PRE>
  	Keystroke Commands 
  <P>
  ?	Print help
  p	Print photometry for star nearest the cursor
  l	List the current psf stars
  a	Add star nearest cursor to psf star list
  f	Fit the psf
  r	Review the fit for all the psf stars
  s	Subtract fitted psf from psf star nearest cursor
  d	Delete psf star nearest cursor from psf star list
  w	Write the psf to the psf image
  z	Rebuild the psf from scratch
  q	Quit task
  <P>
  	Colon Commands
  <P>
  :p [n]	Print photometry for star n
  :a [n]	Add star n to psf star list
  :d [n]	Delete star n from psf star list
  :s [n]  Subtract fitted psf from psf star n   
  <P>
  	Colon Parameter Editing Commands
  <P>
  # Data dependent parameters which affect the psf computation 
  <P>
  :scale	   [value]	Show/set the image scale (units / pixel)
  :fwhmpsf   [value]	Show/set the fwhm of psf (scale units)
  :datamin   [value]	Show/set the minimum good data value (counts)
  :datamax   [value]	Show/set the maximum good data value (counts)
  :matchrad  [value]	Show/set matching radius (scale units)
  <P>
  # Psf computation parameters
  <P>
  :psfimage   [name,name]	Show/set the psf image and groupfile
  :function   [string]	Show/set the analytic psf function
  :varorder   [integer]	Show/set order of psf function variability
  :nclean	    [integer]	Show/set number of cleaning iterations
  :saturated  [y/n]	Show/set the use saturated star flag
  :psfrad	    [value]	Show/set the psf radius (scale units)
  :fitrad	    [value]	Show/set the fitting radius (scale units)
  <P>
  <P>
  The following cursor commands are available once a star has been selected 
  and the graphics cursor has been activated.
  <P>
  	Interactive Graphics Keystroke Commands
  <P>
  ?    	Print help
  p	Print the photometry for this star
  t	Print the plot parameters and data minimum and maximum
  a	Accept star and proceed
  d	Reject star and select another with image cursor
  m	Plot the default mesh plot for this star
  n	Increase vertical angle by 15 degrees (mesh plot only)
  s	Decrease vertical angle by 15 degrees (mesh plot only)
  w	Decrease horizontal angle by 15 degrees (mesh plot only)
  e	Increase horizontal angle by 15 degrees (mesh plot only)
  c	Plot the default contour plot for this star
  r	Plot the radial profile for this star
  <P>
  <P>
  	Colon Graphics Commands
  <P>
  :m [val] [val]	Set the mesh plot vertical and horizontal viewing angles
  :v [val]        Set the mesh plot vertical viewing angle
  :h [val]        Set the mesh plot horizontal viewing angle
  :c [val] [val]  Set the contour plot floor and ceiling levels
  :l [value]	Set the contour plot floor level
  :u [value]	Set the contour plot ceiling level
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H2><A NAME="s_algorithms">ALGORITHMS</A></H2>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  The PSF is determined from the actual observed brightness values as a function
  of x and y 
  for one or more stars in the frame and stored as a two-component model.
  The first component is an analytic function which approximates
  the light distribution in the cores of the PSF stars. There are
  currently 6 choices for the analytic component of the model:
  "<TT>gauss</TT>", "<TT>moffat15</TT>", "<TT>moffat25</TT>", "<TT>lorentz</TT>", "<TT>penny1</TT>", and "<TT>penny2</TT>".
  The parameters of the analytic component of the psf model are stored
  in the psf image header parameters "<TT>FUNCTION</TT>", "<TT>PSFHEIGH</TT>", "<TT>NPARS</TT>",
  and "<TT>PARN</TT>". The magnitude, size, and centroid of the PSF are stored
  in the image header parameters "<TT>PSFMAG</TT>", "<TT>PSFRAD</TT>", 
  "<TT>XPSF</TT>", "<TT>and </TT>"YPSF"<TT>. If <I>matchbyid</I> is "<TT>no</TT>" or there is no input psf star list "<TT>PSFMAG</TT>" is
  set to the magnitude of the first PSF star in the input photometry file. If <I>matchbyid</I>
  is "<TT>yes</TT>", and there is an input psf star list "<TT>PSFMAG</TT>" is set to the magnitude of the first psf star
  in the psf star list. "<TT>XPSF</TT>" and "<TT>YPSF</TT>" are the center of the image.
  If <I>varorder</I> &gt;= 0,
  the residuals from this fit are stored as a lookup
  table with twice the sampling interval of the original image.
  This lookup table is used as additive corrections from the integrated
  analytic function to actual observed empirical PSF.
  The parameters of the analytic function are computed by fitting
  all the stars weighted by their signal-to-noise.
  so that the signal-to-noise ratio in
  the PSF does not deteriorate as fainter stars are added in. The more
  crowded the field the more PSF stars are required to lower the noise
  generated by neighbor subtraction.
  <P>
  If the <I>varorder</I> parameter in the DAOPARS task is set to 1 or 2, two
  or five additional lookup
  tables containing the first derivatives of the PSF in x and y 
  and the second order derivatives of the image with respect to
  x ** 2, x * y, and y ** 2 are also written.
  This model
  permits the PSF fitting process to take account of smooth linear
  or quadratic changes in the PSF across the frame caused for example by a tilt in
  the detector with respect to the optical axis or low order optical
  aberrations.
  Users of this option should ensure that the PSF varies in a systematic
  way across the frame and that the chosen PSF stars span the entire
  region of interest in the frame. To avoid mistaking
  neighbor stars for variations in the PSF it is recommended that the
  first few iterations of PSF be run with a constant PSF. Only after
  neighbor stars have been subtracted reasonably cleanly should
  the variable PSF option be enabled.
  <P>
  The brightness of any hypothetical pixel at any arbitrary point within
  the PSF is computed as follows. The analytic function 
  is integrated over the area of the pixel, a correction is determined
  by bicubic interpolation within the lookup table and added to the
  integral. Since the values in the table of residuals differ by smaller
  amounts between adjacent grid points than the original brightness data
  would have, the errors in the interpolation are much less than they would
  have been if one  had tried to interpolate directly within the original
  data.
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H2><A NAME="s_guide_to_computing_a_psf_in_a_crowded_field">GUIDE TO COMPUTING A PSF IN A CROWDED FIELD</A></H2>
  <! BeginSection: 'GUIDE TO COMPUTING A PSF IN A CROWDED FIELD'>
  <UL>
  <P>
  The following is a rough guide to the methodology of computing the
  PSF in a crowded field. The procedure outlined below assumes
  that the user can either make use of the IRAF display facilities or
  has access to a local display program. At a minimum the display program
  should be able to display an image, read back the coordinates of objects in the
  image, and mark objects in the image.
  <P>
  The crowded field PSF fitting procedure makes use of many of the
  DAOPHOT tasks. Details on the setup and operation of each task can be found
  in the appropriate manual pages.
  <P>
  <DL>
  <DT><B><A NAME="l_">[1]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[1]'>
  <DD>RUN THE DAOFIND and PHOT TASKS ON THE IMAGE OF INTEREST.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[2]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[2]'>
  <DD>EXAMINE THE IMAGE. Load the image on the display with the IRAF display task.
  Using the display itself, the DAOEDIT task, or the IRAF IMEXAMINE task, estimate the radius
  at which
  the stellar light distribution disappears into the noise for the
  brightest candidate PSF star. Call this parameter <I>psfrad</I> and record it.
  Mark the objects detected by DAOFIND with dots on the image display using the
  IRAF TVMARK
  task. Users at sites with display devices not currently supported by
  IRAF should substitute their local versions of DISPLAY and TVMARK.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[3]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[3]'>
  <DD>SELECT CANDIDATE PSF STARS.
  Good PSF stars should have no neighbors
  within the fitting radius stored in the DAOPARS task parameter <I>fitrad</I>.
  In addition all stars within 1.5 times the psf radius,
  (stored in the DAOPARS task parameter
  <I>psfrad</I>), should be significantly fainter than the candidate star.
  There should be no bad columns, bad rows or blemishes
  near the candidate star. A sufficient number of stars should be
  selected in order to reduce the increased noise resulting from the
  neighbor subtraction process. Users of the variable PSF option should
  take care that the list of PSF stars span the area of interest on the
  image. Twenty-five to thirty stars is not unreasonable in this case.
  <P>
  The task PSTSELECT can be used to preselect candidate PSF stars.
  These candidate PSF stars can be marked on the image display using the
  PDUMP, and TVMARK tasks. Be sure to mark the PSF stars in another
  color from the stars found by DAOFIND. Stars can be added to or
  subtracted from this list interactively when PSF is run.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[4]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[4]'>
  <DD>EXAMINE THE PSF STARS FOR NEIGHBORS MISSED BY DAOFIND AND ADD THESE TO
  THE PHOT FILE.
  Examine the vicinity of the PSF stars on the display checking for neighbor
  stars which do not have dots on them indicating that they were
  missed by DAOFIND.
  If IRAF supports the local display device simply run PHOT interactively
  selecting the missing stars with the image cursor.
  Be sure to use the same set of PHOT parameters used in step [1] with
  the exception of the CENTERPARS
  task parameter <I>calgorithm</I> which should be temporarily set to "<TT>centroid</TT>".
  If IRAF does not support the
  local display generate a list of the approximate coordinates of the
  missing stars.
  Run PHOT in batch mode with this coordinate list as input and with the
  parameters set as described above.
  Create a new PHOT file by using PCONCAT to add the new PHOT output to the
  PHOT output from [1] and renumber using PRENUMBER. Do not resort.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[5]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[5]'>
  <DD>ESTIMATE OF THE PSF.
  Run PSF using the combined PHOT output from [4] and
  the list of candidate stars from [3].
  Write out the PSF image (extension .psf.#) and the psf group file
  (extension .psg.#). The PSF image is the current estimate of the PSF.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[6]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[6]'>
  <DD>FIT ALL THE STARS IN EACH PSF STAR GROUP IN THE ORIGINAL IMAGE.
  Run NSTAR on the image using the output group file (extension .psg.#)
  of [5] as the input photometry list. To help prevent the bumps in the initial
  PSF from interfering with the profile fits in NSTAR, it may
  be necessary to temporarily set the psf radius,
  <I>psfrad</I> in the DAOPARS task,
  to about one pixel greater than the separation of the nearest neighbor
  to a PSF star.
  The fitting radius, <I>fitrad</I> in the
  DAOPARS task, should be sufficiently large to include enough
  pixels for a good fit but not so large as to include any neighbors
  inside the fitting radius.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[7]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[7]'>
  <DD>SUBTRACT ALL THE FITTED STARS FROM THE ORIGINAL IMAGE.
  Run SUBSTAR to subtract the NSTAR results from the original image.
  Use the IRAF DISPLAY task or the local display program to display
  the subtracted image. If you decreased the value of <I>psfrad</I>
  in [6] use this smaller value when you subtract as well.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[8]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[8]'>
  <DD>CHECK FOR PREVIOUSLY INVISIBLE FAINT COMPANIONS.
  Check to see whether the PSF stars and neighbors subtracted
  cleanly or whether there are faint companions that were not previously
  visible before.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[9]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[9]'>
  <DD>APPEND THESE COMPANIONS TO THE PHOT FILE.
  Run PHOT on the faint companions in the subtracted image
  and append the results to the PHOT file created in [4] using PCONCAT.
  Renumber the stars using PRENUMBER.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[10]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[10]'>
  <DD>SUBTRACT ALL THE PSF NEIGHBOR STARS FROM THE ORIGINAL IMAGE.
  Edit the nstar output file (extension .nst.#) removing all the PSF stars
  from the file. The PSF stars is the first one in each group. In the
  near future this will be done with the PEXAMINE task but at the
  moment the text editor can be used for text databases and the TTOOLS
  package task TEDIT can be used for tables. PSELECT can also be used
  to remove stars with specific id numbers. Run SUBSTAR using the edited
  nstar output file as input.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[11]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[11]'>
  <DD>RECOMPUTE THE PSF.
  Run PSF on the subtracted image from [10] using the PHOT file from [9]
  as the input stellar photometry file.
  Temporarily set the minimum good data value, the <I>datamin</I> parameter
  in the DATAPARS task to a large negative number, to avoid the
  enhanced noise where the
  stars were subtracted from triggering the bad pixel detector in PSF.
  A new psf (extension .psf.#) and new psf group file (extension .psg.#)
  will be created. Be sure to increase the <I>psfrad</I> value to the
  original large value found in [2].
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[12]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[12]'>
  <DD>RERUN NSTAR.
  Rerun NSTAR on the original image with the newly created group file
  (extension .psg.#) as the input stellar photometry file and the newly
  computed PSF image (extension .psf.#).
  It should not be necessary to reduce the psf radius as in [6]
  but the fitting radius should be left at a generous number.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[13]</A></B></DT>
  <! Sec='GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' Level=0 Label='' Line='[13]'>
  <DD>REPEAT STEPS [7-12] UNTIL THE PSF FIT IS ACCEPTABLE.
  If any neighbors are still visible iterate on this process by repeating
  steps [7] to [12] until the neighbors completely disappear. The main
  point to remember is that each time through the loop the PSF is obtained
  from an image in which the neighbors but not the PSF stars have been 
  subtracted out while NSTAR and SUBSTAR should be run on the original
  picture with all the stars still in it.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'GUIDE TO COMPUTING A PSF IN A CROWDED FIELD'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute the PSF for the image dev$ypix. Select stars using the display and
  the image cursor and show plots of the data and the residuals from the fit
  for each star. Good stars for making the PSF model can be found at (442,410),
  (348,189), and (379,67).
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
  </PRE>
  <P>
  <P>
  2. Run PSF non-interactively using the photometry file and psf star file
  created in the previous example.
  <P>
  <PRE>
  	da&gt; psf dev$ypix default default default default default \<BR>
              psfrad=9.0 fitrad=3.0 interactive- plotfile=psf.plots
  <P>
          ... the output will appear in ypix.psf.2, ypix.psg.2, and
  	    ypix.pst.2
  <P>
          da&gt; gkidir psf.plots
  <P>
          ... list the plots created by psf 
  <P>
          da&gt; gkiextract psf.plots 1 | stdgraph
  <P>
          ... display the surface plots of the first psf star
  <P>
  	da&gt; seepsf ypix.psf.2 ypixpsf
  <P>
  	... convert the sampled PSF look-up table to a PSF image
  </PRE>
  <P>
  <P>
  3. Setup and run PSF interactively without using the image display cursor.
  Use the photometry file created in example 1. Before running PSF in this
  manner the user should have a list of the candidate PSF star ids.
  <P>
  <PRE>
  	da&gt; show stdimcur
  <P>
  	... store the default value
  <P>
  	da&gt; set stdimcur = text
  <P>
  	... define the image cursor to be the standard input
  <P>
  	da&gt; epar psf
  <P>
  	... edit the psf parameters
  <P>
  	... move to the datapars line and type :e edit the data dependent
  	    parameters, type :q to quit the datapars menu
  <P>
  	... move to the daopars line and type :e edit the daophot fitting
    	    parameters, type :q to quit the daopars menu
  <P>
  	... finish editing the psf parameters
  <P>
  	da&gt; psf dev$ypix default "" default default default \<BR>
  	    plottype=radial
  <P>
  	... verify critical parameters
  <P>
  	... type :a # where # stands for the id number of the star,
  	    a plot of the stellar data appears
  <P>
  	... type a to accept the star, d to reject it
  <P>
  	... repeat for all the PSF stars
  <P>
  	... type l to list the psf stars
  <P>
  	... type f to fit the PSF
  <P>
  	... type :s # where # stands for the id of the psf star, a plot
  	    of the model residuals appears
  <P>
  	... type w to save the PSF
  <P>
  	... type q to quit PSF and q again to confirm the quit
  <P>
  	... the output will appear in ypix.psf.3, ypix.pst.3, ypix.psg.3
  <P>
  	da&gt; set stdimcur = stdimage
  <P>
  	... reset the image cursor
  </PRE>
  <P>
  <P>
  4. Run PSF in non-interactive mode using an image cursor  command file of
  instructions called icmds.
  <P>
  <PRE>
  	da&gt; type icmds 
  	    :a 106
  	    :a 24
  	    :a 16
  	    :a 68
  	    f
  	    w
  	    q
  <P>
  	da&gt; psf dev$ypix default "" default default default  \<BR>
  	    icommands=icmds
  <P>
  	... verify the critical parameters
  <P>
  	... the PSF will be constructed from stars 106, 24, 16, 68
  	    in the input photometry file
  <P>
  	... the output will appear in ypix.psf.4, ypix.pst.4, ypix.psg.4
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
  datapars,daopars,pstselect,seepsf
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'GUIDE TO COMPUTING A PSF IN A CROWDED FIELD' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>