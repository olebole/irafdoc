dofoe — Process Fiber Optic Echelle (FOE) spectra
=================================================

**Package: echelle**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>dofoe (Feb93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.echelle</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>dofoe (Feb93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>dofoe</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  dofoe -- Fiber Optic Echelle (FOE) data reduction task
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  dofoe objects
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_summary">SUMMARY</A></H2>
  <! BeginSection: 'SUMMARY'>
  <UL>
  The <B>dofoe</B> reduction task is specialized for scattered light
  subtraction, extraction, flat fielding, and wavelength calibration of Fiber
  Optic Echelle (FOE) spectra.  There may be one fiber or two fibers where
  the second fiber is illuminated by an arc calibration during arc and object
  exposures and a flat field during flat field exposures.  It is a command
  language script which collects and combines the functions and parameters of
  many general purpose tasks to provide a single complete data reduction
  path.  The task provides a degree of guidance, automation, and record
  keeping necessary when dealing with the complexities of reducing this type
  of data.
  </UL>
  <! EndSection:   'SUMMARY'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_objects">objects</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='objects' Line='objects'>
  <DD>List of object spectra to be processed.  Previously processed spectra are
  ignored unless the <I>redo</I> flag is set or the <I>update</I> flag is set and
  dependent calibration data has changed.  Extracted spectra are ignored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apref">apref = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apref' Line='apref = ""'>
  <DD>Aperture reference spectrum.  This spectrum is used to define the basic
  extraction apertures and is typically a flat field spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_flat">flat = "<TT></TT>" (optional)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flat' Line='flat = "" (optional)'>
  <DD>Flat field spectrum.  If specified the one dimensional flat field spectrum
  is extracted and used to make flat field calibrations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_arcs">arcs = "<TT></TT>" (at least one if dispersion correcting)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='arcs' Line='arcs = "" (at least one if dispersion correcting)'>
  <DD>List of arc spectra.  The first arc in the list is used to create a
  dispersion solution interactively.  All other arc spectra will be
  automatically reidentified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_arctable">arctable = "<TT></TT>" (optional) (refspectra)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='arctable' Line='arctable = "" (optional) (refspectra)'>
  <DD>Table defining arc spectra to be assigned to object spectra (see
  <B>refspectra</B>).  If not specified an assignment based on a header
  parameter, <I>params.sort</I>, such as the observation time is made.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_readnoise">readnoise = "<TT>0.</TT>" (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='readnoise' Line='readnoise = "0." (apsum)'>
  <DD>Read out noise in photons.  This parameter defines the minimum noise
  sigma.  It is defined in terms of photons (or electrons) and scales
  to the data values through the gain parameter.  A image header keyword
  (case insensitive) may be specified to get the value from the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gain">gain = "<TT>1.</TT>" (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain = "1." (apsum)'>
  <DD>Detector gain or conversion factor between photons/electrons and
  data values.  It is specified as the number of photons per data value.
  A image header keyword (case insensitive) may be specified to get the value
  from the image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_datamax">datamax = INDEF (apsum.saturation)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datamax' Line='datamax = INDEF (apsum.saturation)'>
  <DD>The maximum data value which is not a cosmic ray.
  When cleaning cosmic rays and/or using variance weighted extraction
  very strong cosmic rays (pixel values much larger than the data) can
  cause these operations to behave poorly.  If a value other than INDEF
  is specified then all data pixels in excess of this value will be
  excluded and the algorithms will yield improved results.
  This applies only to the object spectra and not the flat field or
  arc spectra.  For more
  on this see the discussion of the saturation parameter in the
  <B>apextract</B> package.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_norders">norders = 12 (apfind)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='norders' Line='norders = 12 (apfind)'>
  <DD>Number of orders to be found.  This number is used during the automatic
  definition of the apertures from the aperture reference spectrum.  Note
  that when there is a second fiber for simultaneous arcs the specified
  number will be automatically doubled for finding both sets of orders.
  So in either case specify only the number of orders from a single fiber.
  The interactive review of the aperture assignments allows verification
  and adjustments to the automatic aperture definitions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_width">width = 4. (apedit)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='width' Line='width = 4. (apedit)'>
  <DD>Approximate base full width of the fiber profiles.  This parameter is used
  for the profile centering algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_arcaps">arcaps = "<TT>2x2</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='arcaps' Line='arcaps = "2x2"'>
  <DD>When there is only a single fiber set this parameter to "<TT></TT>".  When there is
  a second fiber used to create simultaneous arcs during the object exposures
  this parameter specifies a list of aperture numbers for the arc fibers.
  Since the object and arc fiber orders are paired the default setting
  expects the even number apertures to be the are apertures.  This should be
  checked interactively.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_fitflat">fitflat = yes (flat1d)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fitflat' Line='fitflat = yes (flat1d)'>
  <DD>Fit and divide the extracted flat field orders by a smooth function
  in order to normalize the wavelength response?  If not done the flat field
  spectral shape (which includes the blaze function) will be divided
  out of the object spectra, thus altering the object data values.
  If done only the small scale response variations are included in the
  flat field and the object spectra will retain their observed flux
  levels and blaze function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_background">background = "<TT>none</TT>" (apsum, apscatter)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background = "none" (apsum, apscatter)'>
  <DD>Type of background light subtraction.  The choices are "<TT>none</TT>" for no
  background subtraction, "<TT>scattered</TT>" for a global scattered light
  subtraction, "<TT>average</TT>" to average the background within background regions,
  "<TT>median</TT>" to use the median in background regions, "<TT>minimum</TT>" to use the
  minimum in background regions, or "<TT>fit</TT>" to fit across the dispersion using
  the background within background regions.  The scattered light option fits
  and subtracts a smooth global background and modifies the input images.
  This is a slow operation and so is NOT performed in quicklook mode.  The
  other background options are local to each aperture at each point along the
  dispersion.  The "<TT>fit</TT>" option uses additional fitting parameters from
  <B>params</B> and the "<TT>scattered</TT>" option uses parameters from <B>apscat1</B>
  and <B>apscat2</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_clean">clean = yes (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clean' Line='clean = yes (apsum)'>
  <DD>Detect and correct for bad pixels during extraction?  This is the same
  as the clean option in the <B>apextract</B> package.  If yes this also
  implies variance weighted extraction and requires reasonably good values
  for the readout noise and gain.  In addition the datamax parameters
  can be useful.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dispcor">dispcor = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dispcor' Line='dispcor = yes'>
  <DD>Dispersion correct spectra?  Depending on the <I>params.linearize</I>
  parameter this may either resample the spectra or insert a dispersion
  function in the image header.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_redo">redo = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='redo' Line='redo = no'>
  <DD>Redo operations previously done?  If no then previously processed spectra
  in the objects list will not be processed (unless they need to be updated).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = no'>
  <DD>Update processing of previously processed spectra if aperture, flat
  field, or dispersion reference definitions are changed?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_batch">batch = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='batch' Line='batch = no'>
  <DD>Process spectra as a background or batch job.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_listonly">listonly = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listonly' Line='listonly = no'>
  <DD>List processing steps but don't process?
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B><A NAME="l_params">params = "<TT></TT>" (pset)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='params' Line='params = "" (pset)'>
  <DD>Name of parameter set containing additional processing parameters.  The
  default is parameter set <B>params</B>.  The parameter set may be examined
  and modified in the usual ways (typically with "<TT>epar params</TT>" or "<TT>:e params</TT>"
  from the parameter editor).  Note that using a different parameter file
  is not allowed.  The parameters are described below.
  </DD>
  </DL>
  <P>
  <CENTER>-- PACKAGE PARAMETERS
  
  </CENTER><BR>
  <P>
  Package parameters are those which generally apply to all task in the
  package.  This is also true of <B>dofoe</B>.
  <DL>
  <DT><B><A NAME="l_observatory">observatory = "<TT>observatory</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = "observatory"'>
  <DD>Observatory at which the spectra were obtained if not specified in the
  image header by the keyword OBSERVAT.  For FOE data the image headers
  identify the observatory as "<TT>kpno</TT>" so this parameter is not used.
  For data from other observatories this parameter may be used
  as describe in <B>observatory</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interp">interp = "<TT>poly5</TT>" (nearest|linear|poly3|poly5|spline3|sinc)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interp' Line='interp = "poly5" (nearest|linear|poly3|poly5|spline3|sinc)'>
  <DD>Spectrum interpolation type used when spectra are resampled.  The choices are:
  <P>
  <PRE>
  	nearest - nearest neighbor
  	 linear - linear
  	  poly3 - 3rd order polynomial
  	  poly5 - 5th order polynomial
  	spline3 - cubic spline
  	   sinc - sinc function
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dispaxis">dispaxis = 2</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dispaxis' Line='dispaxis = 2'>
  <DD>Default dispersion axis.  The dispersion axis is 1 for dispersion
  running along image lines and 2 for dispersion running along image
  columns.  If the image header parameter DISPAXIS is defined it has
  precedence over this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database = "<TT>database</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "database"'>
  <DD>Database (directory) used for storing aperture and dispersion information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print verbose information available with various tasks.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfile">logfile = "<TT>logfile</TT>", plotfile = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "logfile", plotfile = ""'>
  <DD>Text and plot log files.  If a filename is not specified then no log is
  kept.  The plot file contains IRAF graphics metacode which may be examined
  in various ways such as with <B>gkimosaic</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records = ""'>
  <DD>Dummy parameter to be ignored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_version">version = "<TT>ECHELLE: ...</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='version' Line='version = "ECHELLE: ..."'>
  <DD>Version of the package.
  </DD>
  </DL>
  <P>
  <CENTER>PARAMS PARAMETERS
  
  </CENTER><BR>
  <P>
  The following parameters are part of the <B>params</B> parameter set and
  define various algorithm parameters for <B>dofoe</B>.
  <P>
  <CENTER>--  GENERAL PARAMETERS --
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_line">line = INDEF, nsum = 10</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='line' Line='line = INDEF, nsum = 10'>
  <DD>The dispersion line (line or column perpendicular to the dispersion
  axis) and number of adjacent lines (half before and half after unless
  at the end of the image) used in finding, recentering, resizing,
  editing, and tracing operations.  A line of INDEF selects the middle of the
  image along the dispersion axis.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_extras">extras = no (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='extras' Line='extras = no (apsum)'>
  <DD>Include extra information in the output spectra?  When cleaning or using
  variance weighting the cleaned and weighted spectra are recorded in the
  first 2D plane of a 3D image, the raw, simple sum spectra are recorded in
  the second plane, and the estimated sigmas are recorded in the third plane.
  </DD>
  </DL>
  <P>
  <CENTER>-- DEFAULT APERTURE LIMITS --
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_lower">lower = -3., upper = 3. (apdefault)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = -3., upper = 3. (apdefault)'>
  <DD>Default lower and upper aperture limits relative to the aperture center.
  These limits are used when the apertures are first found and may be
  resized automatically or interactively.
  </DD>
  </DL>
  <P>
  <CENTER>-- AUTOMATIC APERTURE RESIZING PARAMETERS --
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_ylevel">ylevel = 0.05 (apresize)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ylevel' Line='ylevel = 0.05 (apresize)'>
  <DD>Data level at which to set aperture limits during automatic resizing.
  It is a fraction of the peak relative to a local background.
  </DD>
  </DL>
  <P>
  <CENTER>-- TRACE PARAMETERS --
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_t_step">t_step = 10 (aptrace)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_step' Line='t_step = 10 (aptrace)'>
  <DD>Step along the dispersion axis between determination of the spectrum
  positions.  Note the <I>nsum</I> parameter is also used to enhance the
  signal-to-noise at each step.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_t_function">t_function = "<TT>spline3</TT>", t_order = 2 (aptrace)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_function' Line='t_function = "spline3", t_order = 2 (aptrace)'>
  <DD>Default trace fitting function and order.  The fitting function types are
  "<TT>chebyshev</TT>" polynomial, "<TT>legendre</TT>" polynomial, "<TT>spline1</TT>" linear spline, and
  "<TT>spline3</TT>" cubic spline.  The order refers to the number of
  terms in the polynomial functions or the number of spline pieces in the spline
  functions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_t_niterate">t_niterate = 1, t_low = 3., t_high = 3. (aptrace)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='t_niterate' Line='t_niterate = 1, t_low = 3., t_high = 3. (aptrace)'>
  <DD>Default number of rejection iterations and rejection sigma thresholds.
  </DD>
  </DL>
  <P>
  <CENTER>-- DEFAULT BACKGROUND PARAMETERS --
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_buffer">buffer = 1. (apscatter)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='buffer' Line='buffer = 1. (apscatter)'>
  <DD>Buffer distance from the edge of any aperture for data to be included
  in the scattered light determination.  This parameter may be modified
  interactively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apscat1">apscat1 = "<TT></TT>", apscat2 = "<TT></TT>" (apscatter)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apscat1' Line='apscat1 = "", apscat2 = "" (apscatter)'>
  <DD>Parameter sets for the fitting functions across and along the dispersion.
  These parameters are those used by <B>icfit</B>.  These parameters are
  usually set interactively.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_b_function">b_function = "<TT>legendre</TT>", b_order = 1 (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_function' Line='b_function = "legendre", b_order = 1 (apsum)'>
  <DD>Default background fitting function and order.  The fitting function types are
  "<TT>chebyshev</TT>" polynomial, "<TT>legendre</TT>" polynomial, "<TT>spline1</TT>" linear spline, and
  "<TT>spline3</TT>" cubic spline.  The order refers to the number of
  terms in the polynomial functions or the number of spline pieces in the spline
  functions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_b_naverage">b_naverage = -100 (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_naverage' Line='b_naverage = -100 (apsum)'>
  <DD>Default number of points to average or median.  Positive numbers
  average that number of sequential points to form a fitting point.
  Negative numbers median that number, in absolute value, of sequential
  points.  A value of 1 does no averaging and each data point is used in the
  fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_b_niterate">b_niterate = 0 (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_niterate' Line='b_niterate = 0 (apsum)'>
  <DD>Default number of rejection iterations.  If greater than zero the fit is
  used to detect deviant fitting points and reject them before repeating the
  fit.  The number of iterations of this process is given by this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_b_low_reject">b_low_reject = 3., b_high_reject = 3. (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_low_reject' Line='b_low_reject = 3., b_high_reject = 3. (apsum)'>
  <DD>Default background lower and upper rejection sigmas.  If greater than zero
  points deviating from the fit below and above the fit by more than this
  number of times the sigma of the residuals are rejected before refitting.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_b_smooth">b_smooth = 10 (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_smooth' Line='b_smooth = 10 (apsum)'>
  <DD>Box car smoothing length for background when using background
  subtraction.  Since the background noise is often the limiting factor
  for good extraction one may box car smooth the background to improve the
  statistics.
  </DD>
  </DL>
  <P>
  <P>
  <CENTER>-- APERTURE EXTRACTION PARAMETERS --
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_weights">weights = "<TT>none</TT>" (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='weights' Line='weights = "none" (apsum)'>
  <DD>Type of extraction weighting.  Note that if the <I>clean</I> parameter is
  set then the weights used are "<TT>variance</TT>" regardless of the weights
  specified by this parameter.  The choices are:
  <DL>
  <DT><B><A NAME="l_">"<TT>none</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"none"'>
  <DD>The pixels are summed without weights except for partial pixels at the
  ends.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>variance</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"variance"'>
  <DD>The extraction is weighted by the variance based on the data values
  and a poisson/ccd model using the <I>gain</I> and <I>readnoise</I>
  parameters.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pfit">pfit = "<TT>fit1d</TT>" (apsum) (fit1d|fit2d)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pfit' Line='pfit = "fit1d" (apsum) (fit1d|fit2d)'>
  <DD>Profile fitting algorithm for cleaning and variance weighted extractions.
  The default is generally appropriate for FOE data but users
  may try the other algorithm.  See <B>approfiles</B> for further information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lsigma">lsigma = 3., usigma = 3. (apsum)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 3., usigma = 3. (apsum)'>
  <DD>Lower and upper rejection thresholds, given as a number of times the
  estimated sigma of a pixel, for cleaning.
  </DD>
  </DL>
  <P>
  <CENTER>-- FLAT FIELD FUNCTION FITTING PARAMETERS --
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_f_interactive">f_interactive = no (fit1d)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='f_interactive' Line='f_interactive = no (fit1d)'>
  <DD>Fit the one dimensional flat field order spectra interactively?
  This is used if <I>fitflat</I> is set and a two dimensional flat field
  spectrum is specified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_f_function">f_function = "<TT>spline3</TT>", f_order = 20 (fit1d)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='f_function' Line='f_function = "spline3", f_order = 20 (fit1d)'>
  <DD>Function and order used to fit the composite one dimensional flat field
  spectrum.  The functions are "<TT>legendre</TT>", "<TT>chebyshev</TT>", "<TT>spline1</TT>", and
  "<TT>spline3</TT>".  The spline functions are linear and cubic splines with the
  order specifying the number of pieces.
  </DD>
  </DL>
  <P>
  <CENTER>-- ARC DISPERSION FUNCTION PARAMETERS --
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_threshold">threshold = 10. (identify/reidentify)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 10. (identify/reidentify)'>
  <DD>In order for a feature center to be determined the range of pixel intensities
  around the feature must exceed this threshold.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coordlist">coordlist = "<TT>linelist$thar.dat</TT>" (ecidentify)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coordlist' Line='coordlist = "linelist$thar.dat" (ecidentify)'>
  <DD>Arc line list consisting of an ordered list of wavelengths.
  Some standard line lists are available in the directory "<TT>linelist$</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_match">match = 1. (ecidentify)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='match' Line='match = 1. (ecidentify)'>
  <DD>The maximum difference for a match between the dispersion function computed
  value and a wavelength in the coordinate list.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_fwidth">fwidth = 4. (ecidentify)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fwidth' Line='fwidth = 4. (ecidentify)'>
  <DD>Approximate full base width (in pixels) of arc lines.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cradius">cradius = 4. (reidentify)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cradius' Line='cradius = 4. (reidentify)'>
  <DD>Radius from previous position to reidentify arc line.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_i_function">i_function = "<TT>chebyshev</TT>", i_xorder = 3, i_yorder = 3 (ecidentify)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='i_function' Line='i_function = "chebyshev", i_xorder = 3, i_yorder = 3 (ecidentify)'>
  <DD>The default function, function order for the pixel position dependence, and
  function order for the aperture number dependence to be fit to the arc
  wavelengths.  The functions choices are "<TT>chebyshev</TT>" or "<TT>legendre</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_i_niterate">i_niterate = 3, i_low = 3.0, i_high = 3.0 (ecidentify)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='i_niterate' Line='i_niterate = 3, i_low = 3.0, i_high = 3.0 (ecidentify)'>
  <DD>Number of rejection iterations and sigma thresholds for rejecting arc
  lines from the dispersion function fits.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_refit">refit = yes (ecreidentify)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refit' Line='refit = yes (ecreidentify)'>
  <DD>Refit the dispersion function?  If yes and there is more than 1 line
  and a dispersion function was defined in the arc reference then a new
  dispersion function of the same type as in the reference image is fit
  using the new pixel positions.  Otherwise only a zero point shift is
  determined for the revised fitted coordinates without changing the
  form of the dispersion function.
  </DD>
  </DL>
  <P>
  <CENTER>-- AUTOMATIC ARC ASSIGNMENT PARAMETERS --
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_select">select = "<TT>interp</TT>" (refspectra)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='select' Line='select = "interp" (refspectra)'>
  <DD>Selection method for assigning wavelength calibration spectra.
  Note that an arc assignment table may be used to override the selection
  method and explicitly assign arc spectra to object spectra.
  The automatic selection methods are:
  <DL>
  <DT><B><A NAME="l_average">average</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='average' Line='average'>
  <DD>Average two reference spectra without regard to any sort parameter.
  If only one reference spectrum is specified then it is assigned with a
  warning.  If more than two reference spectra are specified then only the
  first two are used and a warning is given.
  This option is used to assign two reference spectra, with equal weights,
  independent of any sorting parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_following">following</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='following' Line='following'>
  <DD>Select the nearest following spectrum in the reference list based on the
  sorting parameter.  If there is no following spectrum use the nearest preceding
  spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interp">interp</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='interp' Line='interp'>
  <DD>Interpolate between the preceding and following spectra in the reference
  list based on the sorting parameter.  If there is no preceding and following
  spectrum use the nearest spectrum.  The interpolation is weighted by the
  relative distances of the sorting parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_match">match</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='match' Line='match'>
  <DD>Match each input spectrum with the reference spectrum list in order.
  This overrides the reference aperture check.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Select the nearest spectrum in the reference list based on the sorting
  parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_preceding">preceding</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='preceding' Line='preceding'>
  <DD>Select the nearest preceding spectrum in the reference list based on the
  sorting parameter.  If there is no preceding spectrum use the nearest following
  spectrum.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sort">sort = "<TT>jd</TT>", group = "<TT>ljd</TT>" (refspectra)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sort' Line='sort = "jd", group = "ljd" (refspectra)'>
  <DD>Image header keywords to be used as the sorting parameter for selection
  based on order and to group spectra.
  A null string, "<TT></TT>", or the word "<TT>none</TT>" may be use to disable the sorting
  or grouping parameters.
  The sorting parameter
  must be numeric but otherwise may be anything.  The grouping parameter
  may be a string or number and must simply be the same for all spectra within
  the same group (say a single night).
  Common sorting parameters are times or positions.
  In <B>dofoe</B> the Julian date (JD) and the local Julian day number (LJD)
  at the middle of the exposure are automatically computed from the universal
  time at the beginning of the exposure and the exposure time.  Also the
  parameter UTMIDDLE is computed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_time">time = no, timewrap = 17. (refspectra)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='time' Line='time = no, timewrap = 17. (refspectra)'>
  <DD>Is the sorting parameter a 24 hour time?  If so then the time origin
  for the sorting is specified by the timewrap parameter.  This time
  should precede the first observation and follow the last observation
  in a 24 hour cycle.
  </DD>
  </DL>
  <P>
  <CENTER>-- DISPERSION  CORRECTION PARAMETERS --
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_linearize">linearize = yes (dispcor)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='linearize' Line='linearize = yes (dispcor)'>
  <DD>Interpolate the spectra to a linear dispersion sampling?  If yes the
  spectra will be interpolated to a linear or log linear sampling
  If no the nonlinear dispersion function(s) from the dispersion function
  database are assigned to the input image world coordinate system
  and the spectral data are not interpolated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_log">log = no (dispcor)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='log' Line='log = no (dispcor)'>
  <DD>Use linear logarithmic wavelength coordinates?  Linear logarithmic
  wavelength coordinates have wavelength intervals which are constant
  in the logarithm of the wavelength.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_flux">flux = yes (dispcor)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flux' Line='flux = yes (dispcor)'>
  <DD>Conserve the total flux during interpolation?  If <I>no</I> the output
  spectrum is interpolated from the input spectrum at each output
  wavelength coordinate.  If <I>yes</I> the input spectrum is integrated
  over the extent of each output pixel.  This is slower than
  simple interpolation.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_environment_parameters">ENVIRONMENT PARAMETERS</A></H2>
  <! BeginSection: 'ENVIRONMENT PARAMETERS'>
  <UL>
  The environment parameter <I>imtype</I> is used to determine the extension
  of the images to be processed and created.  This allows use with any
  supported image extension.  For STF images the extension has to be exact;
  for example "<TT>d1h</TT>".
  </UL>
  <! EndSection:   'ENVIRONMENT PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <B>dofoe</B> reduction task is specialized for scattered light
  subtraction, extraction, flat fielding, and wavelength calibration of Fiber
  Optic Echelle (FOE) spectra.  There may be one fiber or two fibers where
  the second fiber is illuminated by an arc calibration during arc and object
  exposures and a flat field during flat field exposures.  When there is
  just one fiber the parameter <I>arcaps</I> is set to "<TT></TT>" and when there are
  two fibers the parameter is used to select which of the defined
  apertures are the orders from the simultaneous arc fiber.
  <P>
  This task is a command language script which collects and combines the
  functions and parameters of many general purpose tasks to provide a single
  complete data reduction path.  The task provides a degree of guidance,
  automation, and record keeping necessary when dealing with the complexities
  of reducing this type of data.
  <P>
  The general organization of the task is to do the interactive setup steps
  first using representative calibration data and then perform the majority
  of the reductions automatically, possibly as a background process, with
  reference to the setup data.  In addition, the task determines which setup
  and processing operations have been completed in previous executions of the
  task and, contingent on the <I>redo</I> and <I>update</I> options, skip or
  repeat some or all the steps.
  <P>
  The description is divided into a quick usage outline followed by details
  of the parameters and algorithms.  The usage outline is provided as a
  checklist and a refresher for those familiar with this task and the
  component tasks.  It presents only the default or recommended usage.  Since
  <B>dofoe</B> combines many separate, general purpose tasks the description
  given here refers to these tasks and leaves some of the details to their
  help documentation.
  <P>
  <B>Usage Outline</B>
  <P>
  <DL>
  <DT><B><A NAME="l_">[1]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[1]'>
  <DD>The images must first be processed with <B>ccdproc</B> for overscan,
  bias, and dark corrections.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[2]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[2]'>
  <DD>Set the <B>dofoe</B> parameters with <B>eparam</B>.  Specify the object
  images to be processed, the flat field image as the aperture reference and
  the flat field, and one or more arc images.  If there are many
  object or arc spectra per setup you might want to prepare "<TT>@ files</TT>".
  Verify and set the format parameters, particularly the number of orders to be
  extracted and processed.  The processing parameters are set
  for simple extraction and dispersion correction but dispersion correction
  can be turned off for quicklook or background subtraction and cleaning
  may be added.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[3]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[3]'>
  <DD>Run the task.  This may be repeated multiple times with different
  observations and the task will generally only do the setup steps
  once and only process new images.  Queries presented during the
  execution for various interactive operations may be answered with
  "<TT>yes</TT>", "<TT>no</TT>", "<TT>YES</TT>", or "<TT>NO</TT>".  The lower case responses apply just
  to that query while the upper case responses apply to all further
  such queries during the execution and no further queries of that
  type will be made.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[4]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[4]'>
  <DD>The apertures are defined using the specified aperture reference image
  which is usually a flat field in which both the object and arc fibers are
  illuminated.  The specified number of orders are found automatically and
  sequential apertures assigned.  The resize option sets the aperture size to
  the widths of the profiles at a fixed fraction of the peak height.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[5]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[5]'>
  <DD>The automatic order identification and aperture assignment is based on peak
  height and may be incorrect.  The interactive aperture editor is entered
  with a plot of the apertures.  When there is a second simultaneous arc
  fiber it is essential that the object and arc
  fiber orders are properly paired with the arc fibers having even aperture
  numbers and the object fibers having odd aperture numbers.  It is also
  required that no orders be skipped in the region of interest.  Missing
  orders are added with the <TT>'m'</TT> key.  Once all orders have been marked the
  aperture numbers are resequenced with <TT>'o'</TT>.  If local background subtraction
  is selected the background regions should be checked with the <TT>'b'</TT> key.
  Preceding this with the <TT>'a'</TT> key allows any changes to the background
  regions to be applied to all orders.  To exit type <TT>'q'</TT>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[6]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[6]'>
  <DD>The order positions at a series of points along the dispersion are measured
  and a function is fit to these positions.  This may be done interactively to
  adjust the fitting parameters.  Not all orders need be examined and the "<TT>NO</TT>"
  response will quit the interactive fitting.  To exit the interactive
  fitting type <TT>'q'</TT>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[7]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[7]'>
  <DD>If flat fielding is to be done the flat field spectra are extracted.  A
  smooth function is fit to each flat field spectrum to remove the large
  scale spectral signature.  The final response spectra are normalized to a
  unit mean over all fibers.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[8]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[8]'>
  <DD>If scattered light subtraction is selected the scattered light parameters
  are set using the aperture reference image and the task <B>apscatter</B>.
  The purpose of this is to interactively define the aperture buffer distance
  for the scattered light and the cross and parallel dispersion fitting
  parameters.  The fitting parameters are taken from and recorded in the
  parameter sets <B>apscat1</B> and <B>apscat2</B>.  All other scattered light
  subtractions are done noninteractively with these parameters.  Note that
  the scattered light correction modifies the input images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[9]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[9]'>
  <DD>If dispersion correction is selected the first arc in the arc list is
  extracted.  One fiber is used to identify the arc lines and define the
  dispersion function using the task <B>ecidentify</B>.  Identify a few arc
  lines in a few orders with <TT>'m'</TT> and <TT>'k'</TT> or <TT>'o'</TT>, use the <TT>'l'</TT> line list
  identification command to automatically add additional lines and fit the
  dispersion function.  Check the quality of the dispersion function fit
  with <TT>'f'</TT>.  When satisfied exit with <TT>'q'</TT>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[10]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[10]'>
  <DD>If there is a second fiber the dispersion function is automatically
  determined using the task <B>ecreidentify</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[11]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[11]'>
  <DD>The arc reference spectrum is dispersion corrected.
  If the spectra are resampled to a linear dispersion system
  (which will be the same for all spectra) the dispersion parameters
  determined from the dispersion solution are printed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[12]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[12]'>
  <DD>The object spectra are now automatically background subtracted (an
  alternative to scattered light subtraction), extracted, flat fielded,
  and dispersion corrected.  Any new dispersion function reference arcs
  assigned to the object images are automatically extracted and
  dispersion functions determined.  A zero point wavelength correction
  is computed from the simultaneous arc fiber spectrum and applied to
  the object spectrum if orders from the second fiber have been identified
  with the <I>arcaps</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">[13]</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='[13]'>
  <DD>The final spectra will have the same name as the original 2D images
  with a "<TT>.ec</TT>" extension added.
  </DD>
  </DL>
  <P>
  <B>Spectra and Data Files</B>
  <P>
  The basic input consists of single or dual fiber FOE object and calibration
  spectra stored as IRAF images.  The <I>arcaps</I> parameter is used to
  discriminate between the two cases.  The type of image format is defined by
  the environment parameter <I>imtype</I>.  Only images with that extension
  will be processed and created.  The raw CCD images must be processed to
  remove overscan, bias, and dark count effects.  This is generally done
  using the <B>ccdred</B> package.  Flat fielding is generally not done at
  this stage but as part of <B>dofoe</B>.  The calibration spectra are flat
  field observations in all fibers, comparison arc lamp spectra in all
  fibers, and, for dual fiber model, arc spectra in one fiber while the
  second fiber observes the object.  If for some reason the flat field or
  calibration arc spectra have separate exposures for the two fibers the
  separate exposures may simply be added.
  <P>
  The assignment of arc calibration exposures to object exposures is
  generally done by selecting the nearest in time and interpolating.
  However, the optional <I>arc assignment table</I> may be used to explicitly
  assign arc images to specific objects.  The format of this file is
  described in the task <B>refspectra</B>.
  <P>
  The final reduced spectra are recorded in two or three dimensional IRAF
  images.  The images have the same name as the original images with an added
  "<TT>.ec</TT>" extension.  Each line in the reduced image is a one dimensional
  spectrum (an echelle order) with associated aperture and wavelength
  information.  When the <I>extras</I> parameter is set the lines in the
  third dimension contain additional information (see
  <B>apsum</B> for further details).  These spectral formats are accepted by the
  one dimensional spectroscopy tasks such as the plotting tasks <B>splot</B>
  and <B>specplot</B>.  The special task <B>scopy</B> may be used to extract
  specific apertures or to change format to individual one dimensional
  images.  The task <B>scombine</B> is used to combine or merge orders into
  a single spectrum.
  <P>
  <B>Package Parameters</B>
  <P>
  The <B>echelle</B> package parameters set parameters affecting all the tasks
  in the package.  Some of the parameters are not applicable to the
  <B>dofoe</B> task.  The observatory parameter is only required for data
  without an OBSERVAT header parameter (currently included in NOAO data).
  The spectrum interpolation type might be changed to "<TT>sinc</TT>" but with the
  cautions given in <B>onedspec.package</B>.  The dispersion axis parameter is
  only needed if a DISPAXIS image header parameter is not defined.  The other
  parameters define the standard I/O functions.  The verbose parameter
  selects whether to print everything which goes into the log file on the
  terminal.  It is useful for monitoring what the <B>dofoe</B> task does.  The
  log and plot files are useful for keeping a record of the processing.  A
  log file is highly recommended.  A plot file provides a record of
  apertures, traces, and extracted spectra but can become quite large.
  The plotfile is most conveniently viewed and printed with <B>gkimosaic</B>.
  <P>
  <B>Processing Parameters</B>
  <P>
  The input images are specified by image lists.  The lists may be
  a list of explicit, comma separate image names, @ files, or image
  templates using pattern matching against file names in the directory.
  The aperture reference spectrum is used to find the orders and trace
  them.  Thus, this requires an image with good signal in both fibers
  which usually means a flat field spectrum.  It is recommended that
  flat field correction be done using one dimensional extracted spectra
  rather than as two dimensional images.  This is done if a flat field
  spectrum is specified.  The arc assignment table is used to specifically
  assign arc spectra to particular object spectra and the format
  of the file is described in <B>refspectra</B>.
  <P>
  The detector read out noise and gain are used for cleaning and variance
  (optimal) extraction.  The dispersion axis defines the wavelength direction
  of spectra in the image if not defined in the image header by the keyword
  DISPAXIS.  The width parameter (in pixels) is used for the profile
  centering algorithm (<B>center1d</B>).
  <P>
  The number of orders selects the number of orders for a single
  fiber and "<TT>pairs</TT>" of object and arc
  fiber profiles for dual fibers.   The number specified will be
  automatically found based on the strongest peaks.
  In the  dual fiber case it is important that both elements of a pair be found,
  so no orders be skipped, and the aperture numbers must be sequential with
  arc profiles having even aperture numbers and object profiles having
  odd numbers in the region of interest, the automatic identification is  
  just a starting point for the interactive review.  The even/odd
  relationship between object and arc profiles is set by the <I>arcaps</I>
  parameter and so may be reversed if desired.
  <P>
  The next set of parameters select the processing steps and options.  The
  flat fitting option allows fitting and removing the overall shape of the
  flat field spectra while preserving the pixel-to-pixel response
  corrections.  This is useful for maintaining the approximate object count
  levels, including the blaze function, and not introducing the reciprocal of
  the flat field spectrum into the object spectra.  If not selected the flat
  field will remove the blaze function from the observations and introduce
  some wavelength dependence from the flat field lamp spectrum.
  <P>
  The <I>background</I> option selects the type of correction for background or
  scattered light.  If the type is "<TT>scattered</TT>" a global scattered light is
  fit to the data between the apertures  and subtracted from the images.
  <I>Note that the input images are modified by this operation</I>.  This
  option is slow.  Alternatively, a local background may be subtracted using
  background regions defined for each aperture.  The data in the regions may
  be averaged, medianed, or the minimum value used.  Another choice is to fit
  the data in the background regions by a function and interpolate to the
  object aperture.
  <P>
  The <I>clean</I> option invokes a profile fitting and deviant point rejection
  algorithm as well as a variance weighting of points in the aperture.  These
  options require knowing the effective (i.e. accounting for any image
  combining) read out noise and gain.  For a discussion of cleaning and
  variance weighted extraction see <B>apvariance</B> and <B>approfiles</B>.
  <P>
  The dispersion correction option selects whether to extract arc spectra,
  determine a dispersion function, assign them to the object spectra, and,
  possibly, resample the spectra to a linear (or log-linear) wavelength
  scale.
  <P>
  Generally once a spectrum has been processed it will not be reprocessed if
  specified as an input spectrum.  However, changes to the underlying
  calibration data can cause such spectra to be reprocessed if the
  <I>update</I> flag is set.  The changes which will cause an update are a new
  reference image, new flat field, adding the scattered light option, and a
  new arc reference image.  If all input spectra are to be processed
  regardless of previous processing the <I>redo</I> flag may be used.  Note
  that reprocessing clobbers the previously processed output spectra.
  <P>
  The <I>batch</I> processing option allows object spectra to be processed as
  a background or batch job.  The <I>listonly</I> option prints a summary of
  the processing steps which will be performed on the input spectra without
  actually doing anything.  This is useful for verifying which spectra will
  be affected if the input list contains previously processed spectra.  The
  listing does not include any arc spectra which may be extracted to
  dispersion calibrate an object spectrum.
  <P>
  The last parameter (excluding the task mode parameter) points to another
  parameter set for the algorithm parameters.  The way <B>dofoe</B> works
  this may not have any value and the parameter set <B>params</B> is always
  used.  The algorithm parameters are discussed further in the next section.
  <P>
  <B>Algorithms and Algorithm Parameters</B>
  <P>
  This section summarizes the various algorithms used by the <B>dofoe</B>
  task and the parameters which control and modify the algorithms.  The
  algorithm parameters available to the user are collected in the parameter
  set <B>params</B>.  These parameters are taken from the various general
  purpose tasks used by the <B>dofoe</B> processing task.  Additional
  information about these parameters and algorithms may be found in the help
  for the actual task executed.  These tasks are identified in the parameter
  section listing in parenthesis.  The aim of this parameter set organization
  is to collect all the algorithm parameters in one place separate from the
  processing parameters and include only those which are relevant for
  FOE data.  The parameter values can be changed from the
  defaults by using the parameter editor,
  <PRE>
  <P>
  	cl&gt; epar params
  <P>
  </PRE>
  or simple typing <I>params</I>.  The parameter editor can also be
  entered when editing the <B>dofoe</B> parameters by typing <I>:e
  params</I> or simply <I>:e</I> if positioned at the <I>params</I>
  parameter.
  <P>
  <B>Aperture Definitions</B>
  <P>
  The first operation is to define the extraction apertures, which include the
  aperture width, background regions, and position dependence with
  wavelength, for the object and arc orders of interest.  This is done
  on a reference spectrum which is usually a flat field taken through
  all fibers.  Other spectra will inherit the reference apertures and
  apply a correction for any shift of the orders across the dispersion.
  The reference apertures are defined only once unless the <I>redo</I>
  option is set.
  <P>
  The selected number of orders are found automatically by selecting the
  highest peaks in a cut across the dispersion.  Note that the specified
  number of orders is multiplied by two in defining the apertures when
  there is a second fiber.  Apertures
  are assigned with a limits set by the <I>lower</I> and
  <I>upper</I> parameter and numbered sequentially.  A query is then
  given allowing the aperture limits to be "<TT>resized</TT>" based on the profile
  itself (see <B>apresize</B>).
  <P>
  A cut across the orders is then shown with the apertures marked and
  an interactive aperture editing mode is entered (see <B>apedit</B>).
  For <B>dofoe</B> the aperture identifications and numbering is particularly
  critical.  When there is a single fiber the aperture numbers must
  be sequential with the order numbers.  If an order is skipped then the
  aperture number must also be skipped.
  <P>
  For dual fibers all "<TT>pairs</TT>" of object and arc orders in the region of
  interest must be defined without skipping any orders.  The orders must
  also be numbered sequentially (though the direction does not matter)
  so that the arc apertures are either all even or all odd as defined
  by the <I>arcaps</I> parameter (the default is even numbers for the
  arc apertures).  The <TT>'o'</TT> key will provide the necessary reordering.
  <P>
  If local background subtraction is used the background regions should
  also be checked with the <TT>'b'</TT> key.  Typically one adjusts all
  the background regions at the same time by selecting all apertures with
  the <TT>'a'</TT> key first.  To exit the background and aperture editing steps type
  <TT>'q'</TT>.
  <P>
  Next the positions of the orders at various points along the dispersion are
  measured and "<TT>trace functions</TT>" are fit.  The user is asked whether to fit
  each trace function interactively.  This is selected to adjust the fitting
  parameters such as function type and order.  When interactively fitting a
  query is given for each aperture.  After the first aperture one may skip
  reviewing the other traces by responding with "<TT>NO</TT>".  Queries made by
  <B>dofoe</B> generally may be answered with either lower case "<TT>yes</TT>" or "<TT>no</TT>"
  or with upper case "<TT>YES</TT>" or "<TT>NO</TT>".  The upper case responses apply to all
  further queries and so are used to eliminate further queries of that kind.
  <P>
  The above steps are all performed using tasks from the <B>apextract</B>
  package and parameters from the <B>params</B> parameters.  As a quick
  summary, the dispersion direction of the spectra are determined from the
  package <B>dispaxis</B> parameter if not defined in the image header.  The
  default line or column for finding the orders and the number of image lines
  or columns to sum are set by the <I>line</I> and <I>nsum</I> parameters.  A
  line of INDEF (the default) selects the middle of the image.  The automatic
  finding algorithm is described for the task <B>apfind</B> and basically
  finds the strongest peaks.  The resizing is described in the task
  <B>apresize</B> and the parameters used are also described there and
  identified in the PARAMETERS section.  The tracing is done as described in
  <B>aptrace</B> and consists of stepping along the image using the specified
  <I>t_step</I> parameter.  The function fitting uses the <B>icfit</B> commands
  with the other parameters from the tracing section.
  <P>
  <B>Background or Scattered Light Subtraction</B>
  <P>
  In addition to not subtracting any background scattered light there are two
  approaches to subtracting this light.  The first is to determine a smooth
  global scattered light component.  The second is to subtract a locally
  determined background at each point along the dispersion and for each
  aperture.  Note that background subtraction is only done for object images
  and not for arc images.
  <P>
  The global scattered light fitting and subtraction is done with the task
  <B>apscatter</B>.  The function fitting parameters are set interactively
  using the aperture reference spectrum.  All other subtractions are done
  noninteractively with the same set of parameters.  The scattered light is
  subtracted from the input images, thus modifying them, and one might wish
  to first make backups of the original images.
  <P>
  The scattered light is measured between the apertures using a specified
  buffer distance from the aperture edges.  The scattered light pixels are
  fit by a series of one dimensional functions across the dispersion.  The
  independent fits are then smoothed along the dispersion by again fitting
  low order functions.  These fits then define the smooth scattered light
  surface to be subtracted from the image.  The fitting parameters are
  defined and recorded in the two parameter sets <I>apscat1</I> and
  <I>apscat2</I>.  The scattered light algorithm is described more fully in
  <B>apscatter</B>.  This algorithm is relatively slow.
  <P>
  Local background subtraction is done during extraction based on background
  regions and parameters defined by the default background parameters or
  changed during interactive review of the apertures.  The background
  subtraction options are to subtract the average, median, or minimum of the
  pixels in the background regions, or to fit a function and subtract the
  function from under the extracted object pixels.  The background regions
  are specified in pixels from the aperture center and follow changes in
  center of the spectrum along the dispersion.  The syntax is colon separated
  ranges with multiple ranges separated by a comma or space.  The background
  fitting uses the <B>icfit</B> routines which include medians, iterative
  rejection of deviant points, and a choice of function types and orders.
  Note that it is important to use a method which rejects cosmic rays such as
  using either medians over all the background regions (<I>background</I> =
  "<TT>median</TT>") or median samples during fitting (<I>b_naverage</I> &lt; -1).
  The background smoothing parameter <I>b_smooth</I> is may be used
  to provide some additional local smoothing of the background light.
  The background subtraction algorithm and options are described in greater
  detail in <B>apsum</B> and <B>apbackground</B>.
  <P>
  <B>Extraction</B>
  <P>
  The actual extraction of the spectra is done by summing across the fixed
  width apertures at each point along the dispersion.  The default is to
  simply sum the pixels using partial pixels at the ends.  There is an
  option to weight the sum based on a Poisson noise model using the
  <I>readnoise</I> and <I>gain</I> detector parameters.  Note that if the
  <I>clean</I> option is selected the variance weighted extraction is used
  regardless of the <I>weights</I> parameter.  The sigma threshold for
  cleaning are also set in the <B>params</B> parameters.
  <P>
  The cleaning and variance weighting options require knowing the effective
  (i.e. accounting for any image combining) read out noise and gain.  These
  numbers need to be adjusted if the image has been processed such that the
  intensity scale has a different origin (such as a scattered light
  subtraction) or scaling (such as caused by unnormalized flat fielding).
  These options also require using background subtraction if the profile does
  not go to zero.  For optimal extraction and cleaning to work it is
  recommended that any scattered light be accounted for by local background
  subtraction rather than with the scattered light subtraction and the
  <I>fitflat</I> option be used.  The <I>b_smooth</I> parameter is also
  appropriate in this application and improves the optimal extraction results
  by reducing noise in the background signal.  For further discussion of
  cleaning and variance weighted extraction see <B>apvariance</B> and
  <B>approfiles</B> as well as  <B>apsum</B>.
  <P>
  <B>Flat Field Correction</B>
  <P>
  Flat field corrections may be made during the basic CCD processing; i.e.
  direct division by the two dimensional flat field observation.  In that
  case do not specify a flat field spectrum; use the null string "<TT></TT>".  The
  <B>dofoe</B> task provides an alternative flat field response correction
  based on division of the extracted object spectra by the extracted flat field
  spectra.  A discussion of the theory and merits of flat fielding directly
  verses using the extracted spectra will not be made here.  The
  <B>dofoe</B> flat fielding algorithm is the <I>recommended</I> method for
  flat fielding since it works well and is not subject to the many problems
  involved in two dimensional flat fielding.
  <P>
  The first step is extraction of the flat field spectrum, if one is specified,
  using the reference apertures.  Only one flat field is allowed so if
  multiple flat fields are required the data must be reduced in groups.  When
  the <I>fitflat</I> option is selected (the default) the extracted flat field
  spectra are fit by smooth functions and the ratio of the flat field spectra
  to the smooth functions define the response spectra.  The default fitting
  function and order are given by the parameters <I>f_function</I> and
  <I>f_order</I>.  If the parameter <I>f_interactive</I> is "<TT>yes</TT>" then the
  fitting is done interactively using the <B>fit1d</B> task which uses the
  <B>icfit</B> interactive fitting commands.
  <P>
  If the <I>fitflat</I> option is not selected the extracted and globally
  normalized flat field spectra are directly divided in the object spectra.
  This removes the blaze function, thus altering the data counts, and
  introduces the reciprocal of the flat field spectrum in the object
  spectra.
  <P>
  The final step is to normalize the flat field spectra by the mean counts over
  all the fibers.  This normalization step is simply to preserve the average
  counts of the extracted object and arc spectra after division by the
  response spectra.
  <P>
  <B>Dispersion Correction</B>
  <P>
  If dispersion correction is not selected, <I>dispcor</I>=no, then the object
  spectra are simply extracted.  If it is selected the arc spectra are used
  to dispersion calibrate the object spectra.  There are three steps involved;
  determining the dispersion functions relating pixel position to wavelength,
  assigning the appropriate dispersion function to a particular observation,
  and either storing the nonlinear
  dispersion function in the image headers or resampling the spectra to
  evenly spaced pixels in wavelength.  When there are two fibers there is
  also a step of applying a zero point correction to the object fiber based
  on the arc fiber.
  <P>
  The first arc spectrum in the arc list is used to define the reference
  dispersion solution.  It is extracted using the reference aperture
  definitions.  Note extractions of arc spectra are not background or
  scattered light subtracted.  The interactive task <B>ecidentify</B> is used
  to define the dispersion function in one fiber.  The idea is to mark some
  lines in a few orders whose wavelengths are known (with the line list used
  to supply additional lines after the first few identifications define the
  approximate wavelengths) and to fit a function giving the wavelength from
  the aperture number and pixel position.  The dispersion function for the
  second fiber, if one is present, is then determined automatically by
  reference to the first fiber using the task <B>ecreidentify</B>.
  <P>
  The arc dispersion function parameters are for <B>ecidentify</B> and it's
  related partner <B>ecreidentify</B>.  The parameters define a line list for
  use in automatically assigning wavelengths to arc lines, a centering width
  (which should match the line widths at the base of the lines), the
  dispersion function type and orders, parameters to exclude bad lines from
  function fits, and defining whether to refit the dispersion function as
  opposed to simply determining a zero point shift.  The defaults should
  generally be adequate and the dispersion function fitting parameters may be
  altered interactively.  One should consult the help for the two tasks for
  additional details of these parameters and the interactive operation of
  <B>ecidentify</B>.
  <P>
  Once the reference dispersion functions are defined other arc spectra are
  extracted as they are assign to the object spectra.  The assignment of
  arcs is done either explicitly with an arc assignment table (parameter
  <I>arctable</I>) or based on a header parameter such as a time.
  The assignments are made by the task <B>refspectra</B>.  When two arcs are
  assigned to an object spectrum an interpolation is done between the two
  dispersion functions.  This makes an approximate correction for steady
  drifts in the dispersion.
  <P>
  When a second arc fiber monitors any zero point shifts in the dispersion
  functions it is probably only necessary to have one or two arc spectra, one
  at the beginning and/or one at the end of the night.
  <P>
  The tasks <B>setjd</B> and <B>setairmass</B> are automatically run on all
  spectra.  This computes and adds the header parameters for the Julian date
  (JD), the local Julian day number (LJD), the universal time (UTMIDDLE), and
  the air mass at the middle of the exposure.  The default arc assignment is
  to use the Julian date grouped by the local Julian day number.  The
  grouping allows multiple nights of data to be correctly assigned at the
  same time.
  <P>
  Defining the dispersion function for a new arc extraction is done with
  the task <B>ecreidentify</B>.  This is done noninteractively with log
  information recorded about the line reidentifications and the fit.
  <P>
  When there are two fibers there are two full dispersion function from the
  single or pair of arc spectra, one for the object fiber and one for the arc
  fiber.  When an object spectrum is extracted so is the simultaneous arc
  spectrum.  A zero point shift of the arc spectrum relative to the
  dispersion solution of the dual arc observation is computed using
  <B>ecreidentify</B> (<I>refit</I>=no).  This zero point shift is assumed to
  be the same for the object fiber and it is added to the dispersion function
  of the dual arc observation for the object fiber.  Note that this does not
  assume that the object and arc fiber dispersion functions are the same or
  have the same wavelength origin, but only that the same shift in wavelength
  zero point applies to both fibers.  Once the dispersion function correction
  is determined from the extracted arc fiber spectrum it is deleted leaving
  only the object spectrum.
  <P>
  The last step of dispersion correction is setting the dispersion
  of the object spectrum.  There are two choices here.
  If the <I>linearize</I> parameter is not set the nonlinear dispersion
  function is stored in the image header.  Other IRAF tasks interpret
  this information when dispersion coordinates are needed for plotting
  or analysis.  This has the advantage of not requiring the spectra
  to be interpolated and the disadvantage that the dispersion
  information is only understood by IRAF tasks and cannot be readily
  exported to other analysis software.
  <P>
  If the <I>linearize</I> parameter is set then the spectra are resampled to a
  linear dispersion relation either in wavelength or the log of the
  wavelength.  For echelle spectra each order is linearized independently so
  that the wavelength interval per pixel is different in different orders.
  This preserves most of the resolution and avoids over or under sampling of
  the highest or lowest dispersion orders.  The wavelength limits are
  taken from the limits determined from the arc reference spectrum and
  the number of pixels is the same as the original images.  The dispersion
  per pixel is then derived from these constraints.
  <P>
  The linearization algorithm  parameters allow selecting the interpolation
  function type, whether to conserve flux per pixel by integrating across the
  extent of the final pixel, and whether to linearize to equal linear or
  logarithmic intervals.  The latter may be appropriate for radial velocity
  studies.  The default is to use a fifth order polynomial for interpolation,
  to conserve flux, and to not use logarithmic wavelength bins.  These
  parameters are described fully in the help for the task <B>dispcor</B> which
  performs the correction.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  The following example uses artificial data and may be executed
  at the terminal (with IRAF V2.10).  This is also the sequence performed
  by the test procedure "<TT>demos dofoe</TT>".  Because the images are small the
  dispersion solution is somewhat simplistic.
  <P>
  <PRE>
  ec&gt; demos mkdofoe
  Creating image demoobj ...
  Creating image demoflat ...
  Creating image demoarc ...
  ec&gt; echelle.verbose = yes
  ec&gt; dofoe demoobj apref=demoflat flat=demoflat arcs=demoarc \<BR>
  &gt;&gt;&gt; norders=3 width=5.
  Set reference apertures for demoflat
  Searching aperture database ...
  Finding apertures ...
  Mar  4  9:39: FIND - 6 apertures found for demoflat
  Resize apertures for demoflat?  (yes):
  Resizing apertures ...
  Mar  4  9:39: RESIZE - 6 apertures resized for demoflat
  &lt;Review aperture assignments.  Exit with <TT>'q'</TT>&gt;
  Fit traced positions for demoflat interactively?  (yes):
  Tracing apertures ...
  Fit curve to aperture 1 of demoflat interactively  (yes):
  &lt;Review trace and fit. Exit with <TT>'q'</TT>&gt;
  Fit curve to aperture 2 of demoflat interactively  (yes): N
  Mar  4  9:39: TRACE - 6 apertures traced in demoflat.
  Mar  4  9:39: DATABASE - 6 apertures for demoflat written to database
  Create response function demoflatnorm.ec
  Extract flat field demoflat
  Searching aperture database ...
  Mar  4  9:39: DATABASE  - 6 apertures read for demoflat from database
  Extracting apertures ...
  Mar  4  9:39: EXTRACT - Aperture 1 from demoflat --&gt; demoflat.ec
  Mar  4  9:39: EXTRACT - Aperture 2 from demoflat --&gt; demoflat.ec
  Mar  4  9:39: EXTRACT - Aperture 3 from demoflat --&gt; demoflat.ec
  Mar  4  9:39: EXTRACT - Aperture 4 from demoflat --&gt; demoflat.ec
  Mar  4  9:39: EXTRACT - Aperture 5 from demoflat --&gt; demoflat.ec
  Mar  4  9:40: EXTRACT - Aperture 6 from demoflat --&gt; demoflat.ec
  Fit and ratio flat field demoflat
  Create the normalized response demoflatnorm.ec
  demoflatnorm.ec -&gt; demoflatnorm.ec  using bzero: 0.  and bscale: 1.
      mean: 1.  median: 0.9990048  mode: 0.9876572
      upper: INDEF  lower: INDEF
  Extract arc reference image demoarc
  Mar  4  9:40: DATABASE  - 6 apertures read for demoflat from database
  Mar  4  9:40: DATABASE - 6 apertures for demoarc written to database
  Mar  4  9:40: EXTRACT - Aperture 1 from demoarc --&gt; demoarc.ec
  Mar  4  9:40: EXTRACT - Aperture 2 from demoarc --&gt; demoarc.ec
  Mar  4  9:40: EXTRACT - Aperture 3 from demoarc --&gt; demoarc.ec
  Mar  4  9:40: EXTRACT - Aperture 4 from demoarc --&gt; demoarc.ec
  Mar  4  9:40: EXTRACT - Aperture 5 from demoarc --&gt; demoarc.ec
  Mar  4  9:40: EXTRACT - Aperture 6 from demoarc --&gt; demoarc.ec
  Determine dispersion solution for demoarc
  &lt;Mark lines with <TT>'m'</TT> and change orders with <TT>'k'</TT>
  &lt;<TT>'m'</TT> line at pixel 78 and assign 4965.
  &lt;<TT>'k'</TT> to order 2
  &lt;<TT>'m'</TT> line at pixel 78 and assign 5009
  &lt;<TT>'m'</TT> line at pixel 78 and assign 5020
  &lt;<TT>'k'</TT> to order 3
  &lt;<TT>'m'</TT> line at pixel 78 and assign 5049.8
  &lt;<TT>'m'</TT> line at pixel 78 and assign 5050.8
  &lt;<TT>'m'</TT> line at pixel 78 and assign 5055.3
  &lt;<TT>'m'</TT> line at pixel 78 and assign 5062
  &lt;<TT>'m'</TT> line at pixel 78 and assign 5064.9
  &lt;<TT>'f'</TT> to fit
  &lt;<TT>'q'</TT> to quit fit and <TT>'q'</TT> to quit ECIDENTIFY
  <P>
  ECREIDENTIFY: NOAO/IRAF V2.10BETA valdes@puppis Wed 09:54:16 04-Mar-92
    Reference image = demoarc.ec, Refit = yes
     Image    Found     Fit Pix Shift  User Shift  Z Shift      RMS
    d...ec    8/8     8/8        1.48        7.06  2.11E-5  0.00879
  d...ec: ap = 1, w1 = 4959.1, w2 = 4978.5, dw = 0.076, nw = 256
  d...ec: ap = 2, w1 = 5003.4, w2 = 5022.1, dw = 0.073, nw = 256
  d...ec: ap = 3, w1 = 5049.0, w2 = 5067.0, dw = 0.070, nw = 256
  Extract object spectrum demoobj
  Searching aperture database ...
  Mar  4  9:54: DATABASE  - 6 apertures read for demoflat from database
  Recentering apertures ...
  Mar  4  9:54: RECENTER  - 6 apertures shifted by -0.03 for demoobj.
  Mar  4  9:54: DATABASE - 6 apertures for demoobj written to database
  Extracting apertures ...
  Mar  4  9:54: EXTRACT - Aperture 1 from demoobj --&gt; demoobj.ec
  Mar  4  9:54: EXTRACT - Aperture 2 from demoobj --&gt; demoobj.ec
  Mar  4  9:54: EXTRACT - Aperture 3 from demoobj --&gt; demoobj.ec
  Mar  4  9:54: EXTRACT - Aperture 4 from demoobj --&gt; demoobj.ec
  Mar  4  9:54: EXTRACT - Aperture 5 from demoobj --&gt; demoobj.ec
  Mar  4  9:54: EXTRACT - Aperture 6 from demoobj --&gt; demoobj.ec
  Assign arc spectra for demoobj
  [demoobj] refspec1='demoarc'
  Reidentify arc fibers in demoobj with respect to demoarc
  <P>
  ECREIDENTIFY: NOAO/IRAF V2.10BETA valdes@puppis Wed 09:54:28 04-Mar-92
    Reference image = demoarcarc.ec, Refit = no
     Image    Found     Fit Pix Shift  User Shift  Z Shift      RMS
    d...ec    8/8     8/8       0.119       0.566  1.69E-6  0.00834
  Dispersion correct demoobj
  d...ec.imh: ap = 1, w1 = 4959.1, w2 = 4978.5, dw = 0.076, nw = 256
  d...ec.imh: ap = 2, w1 = 5003.4, w2 = 5022.1, dw = 0.073, nw = 256
  d...ec.imh: ap = 3, w1 = 5049.0, w2 = 5067.0, dw = 0.070, nw = 256
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_DOFOE">DOFOE V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='DOFOE' Line='DOFOE V2.10.3'>
  <DD>The image format type to be
  processed is selected with the <I>imtype</I> environment parameter.  The
  dispersion axis parameter is now a package parameter.  Images will only
  be processed if the have the CCDPROC keyword.  A <I>datamax</I> parameter
  has been added to help improve cosmic ray rejection.  A scattered
  light subtraction processing option has been added.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  apedit, apfind, approfiles, aprecenter, apresize, apsum, aptrace, apvariance,
  ccdred, center1d, dispcor, fit1d, icfit, ecidentify, observatory,
  onedspec.package, refspectra, ecreidentify, setairmass, setjd
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'SUMMARY' 'PARAMETERS' 'ENVIRONMENT PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>