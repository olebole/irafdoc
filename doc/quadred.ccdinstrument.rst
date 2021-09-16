.. _ccdinstrument:

ccdinstrument — Review and edit instrument translation files
============================================================

**Package: quadred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ccdinstrument -- Setup and verify CCD instrument translation files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  ccdinstrument images
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images to be verified or used to setup a CCD instrument translation
  file.
  </DD>
  </DL>
  <DL>
  <DT><B>instrument = "<TT>)_.instrument</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='instrument' Line='instrument = ")_.instrument"'>
  <DD>CCD instrument translation file.  The default is to use the translation
  file defined in the <B>ccdred</B> package parameters.  Note that one would
  need write permission to update this file though the task has a write
  command to save any changes to a different file.
  </DD>
  </DL>
  <DL>
  <DT><B>ssfile = "<TT>)_.ssfile</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ssfile' Line='ssfile = ")_.ssfile"'>
  <DD>Subset translation file.  The default is to use the file defined in
  the <B>ccdred</B> package parameters.
  </DD>
  </DL>
  <DL>
  <DT><B>edit = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='edit' Line='edit = yes'>
  <DD>Edit the instrument translation file?  If "<TT>yes</TT>" an interactive
  mode is entered allowing translation parameters to be modified while if
  "<TT>no</TT>" the task is simply used to verify the translations noninteractively.
  </DD>
  </DL>
  <DL>
  <DT><B>parameters = "<TT>basic</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='parameters' Line='parameters = "basic"'>
  <DD>Parameters to be displayed.  The choices are "<TT>basic</TT>" to display only the
  most basic parameters (those needed for the simplest automation of
  <B>ccdred</B> tasks),  "<TT>common</TT>" to display the common parameters used
  by the package (most of these are keywords to be written to the image
  rather than translated), and "<TT>all</TT>" to display all the parameters
  referenced by the package including the most obscure.  For most uses
  the "<TT>basic</TT>" set is all that is important and the other options are
  included for completeness.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The purpose of this task is to provide an interface to simplify setting
  up CCD instrument translation files and to verify the translations
  for a set of images.  Before this task was written users who needed to
  set up translation files for new instruments and observatories had
  to directly create the files with an editor.  Many people encountered
  difficulties and were prone to errors.  Also there was no task that
  directly verified the translations though <B>ccdlist</B> provided some
  clues.
  <P>
  The <B>ccdred</B> package was designed to make intelligent use of
  information in image headers for determining things such as image
  calibration or object type and exposure times.  While the package may
  be used without this capability it is much more convenient to be
  able to use information from the image.  The package was also intended
  to be used with many different instruments, detectors, and observatories.
  The key to providing image header access across different observatories
  is the ability to translate the needs of the package to the appropriate
  keywords in the image header.  This is done through a file called
  an "<TT>instrument translation file</TT>".  For a complete description of
  this file and other instrument setup features of the package see
  <B>ccdred.instruments</B>.
  <P>
  The instrument translation file translates the parameter names used by
  the <B>ccdred</B> package into image specific parameters and also
  supplies default values for parameters.  The translation proceeds as
  follows.  When a package task needs a parameter for an image, for
  example "<TT>imagetyp</TT>", it looks in the instrument translation file.  If
  the file is not found or none is specified then the image header
  keyword that is requested is assumed to have the same name.  If an
  instrument translation file is defined then the requested parameter is
  translated to an image header keyword, provided a translation entry is
  given.  If no translation is given the package name is used.  For
  example the package parameter "<TT>imagetyp</TT>" might be translated to
  "<TT>data-typ</TT>" (the old NOAO CCD keyword).  If the parameter is not found
  then the default value specified in the translation file, if present,
  is returned.
  <P>
  For recording parameter information in the header, such
  as processing flags, translation is also used.  For example, if the
  flag specifying that the image has been corrected by a flat field is to
  be set then the package parameter name "<TT>flatcor</TT>" might be translated to
  "<TT>ff-flag</TT>".  If no translation is given then the new image header
  parameter is entered as "<TT>flatcor</TT>".
  <P>
  The CCD image type requires a second level of translation also defined
  in the translation file.  Once the image keyword which identifies the
  type of CCD image, for example a flat field or object, is translated
  to an imahe keyword the specific
  string value must be translated to one of the CCD image types used
  by the package.  The translation works in the same way, the specific
  string found is translated to the <B>ccdred</B> type and returned to
  the task.  This translation is tricky in that the exact string
  including all spaces and capitalizations must be correctly defined
  in the translation file.  The <B>ccdinstrument</B> allows doing
  this automatically thus minimizing typing errors.
  <P>
  The basic display format of the task is a table of five columns
  giving the parameter name used by the package, the image keyword
  to which it is translated, the default value (if any), the value
  the task will receive for the current image after translation,
  and the actual keyword value in the image.  A "<TT>?</TT>" is printed if
  a value cannot be determined.  The idea of the task is to make sure
  that the value a <B>ccdred</B> task sees is the correct one and if not
  to modify the translation appropriately.  In verify mode when the
  <B>edit</B> parameter is not set the translation table is simply
  printed for each input image.
  <P>
  In edit mode the user interactively gives commands at the ccdinstrument
  prompt to display or modify keywords.  The modifications can then be
  written to the instrument file or saved in a private copy.  The
  list of commands is shown below and may be printed using ? or help.
  <P>
  <PRE>
  			CCDINSTRUMENT COMMANDS
  <P>
  ?	    Print command summary
  help	    Print command summary
  imheader    Page image header
  instrument  Print current instrument translation file
  next	    Next image
  newimage    Select a new image
  quit	    Quit
  read	    Read instrument translation file
  show	    Show current translations
  write	    Write instrument translation file
  <P>
  translate   Translate image string selected by the imagetyp
  	    parameter to one of the CCDRED types given as an
  	    argument or queried:
  	    object, zero, dark, flat, comp, illum, fringe, other
  <P>
  </PRE>
  The following are CCDRED parameters which may be translated.  You are
  queried for the image keyword to use or it may be typed after the command.
  An optional default value (returned if the image does not contain the
  keyword) may be typed as the second argument of the command.
  <PRE>
  <P>
  	BASIC PARAMETERS
  imagetyp	Image type parameter (see also translate)
  subset		Subset or filter parameter
  exptime		Exposure time
  darktime	Dark time (may be same as the exposure time)
  </PRE>
  <P>
  The commands may be followed by values such as file names for some of
  the general commands or the keyword and default value for the parameters
  to be translated.  Note this is the only way to specify a default value.
  If no arguments are given the user is prompted with the current value
  which may then be changed.
  <P>
  The set of parameters shown above are only those considered "<TT>basic</TT>".
  In order to avoid confusion the task can limit the set of parameters
  displayed.  Without going into great detail, it is only the basic
  parameters which are generally required to have valid translations to
  allow the package to work well.  However, for completeness, and if someone
  wants to go wild with translations, further parameters may be displayed
  and changed.  The parameters displayed is controlled by the <I>parameters</I>
  keyword.  The additional parameters not shown above are:
  <P>
  <PRE>
  	USEFUL DEFAULT GEOMETRY PARAMETERS
  biassec		Bias section (often has a default value)
  trimsec		Trim section (often has a default value)
  <P>
  	COMMON PROCESSING FLAGS
  fixpix		Bad pixel replacement flag
  overscan	Overscan correction flag
  trim		Trim flag
  zerocor		Zero level correction flag
  darkcor		Dark count correction flag
  flatcor		Flat field correction flag
  <P>
  	RARELY TRANSLATED PARAMETERS
  ccdsec		CCD section
  datasec		Data section
  fixfile		Bad pixel file
  <P>
  fringcor	Fringe correction flag
  illumcor	Ilumination correction flag
  readcor		One dimensional zero level read out correction
  scancor		Scan mode correction flag
  nscanrow	Number of scan rows
  <P>
  illumflt	Ilumination flat image
  mkfringe	Fringe image
  mkillum		Iillumination image
  skyflat		Sky flat image
  <P>
  ccdmean		Mean value
  ccdmeant	Mean value compute time
  fringscl	Fringe scale factor
  ncombine	Number of images combined
  date-obs	Date of observations
  dec		Declination
  ra		Right Ascension
  title		Image title
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To verify the translations for a set of images using the default
  translation file:
  <P>
  <PRE>
  	cl&gt; setinst "" review-
  	cl&gt; ccdinst dev$pix edit-
  	Image: dev$pix
  	Instrument file: 
  	Subset file: subsets
  <P>
  	CCDRED    IMAGE     DEFAULT   CCDRED    IMAGE   
  	PARAM     KEYWORD   VALUE     VALUE     VALUE   
  	--------------------------------
  	imagetyp  imagetyp            none      ?
  	subset    subset                        ?
  	exptime   exptime             ?         ?
  	darktime  darktime            ?         ?
  <P>
  	cl&gt; setinst "" site=kpno dir=ccddb$ review-
  	cl&gt; ccdinst dev$pix edit-
  	Image: dev$pix
  <P>
  	Instrument file: ccddb$kpno/camera.dat
  	Subset file: subsets
  <P>
  	CCDRED    IMAGE     DEFAULT   CCDRED    IMAGE   
  	PARAM     KEYWORD   VALUE     VALUE     VALUE   
  	--------------------------------
  	imagetyp  data-typ            object    OBJECT (0)
  	subset    f1pos               2         2
  	exptime   otime               600       600
  	darktime  ttime               600       600
  </PRE>
  <P>
  2.  Set up an  instrument translation file from scratch.
  <P>
  <PRE>
  	ccdinst ech???.imh instr=myccd edit+
  	Warning: OPEN: File does not exist (myccd)
  	Image: ech001.imh
  	Instrument file: myccd
  	Subset file: subsets
  	
  	CCDRED    IMAGE     DEFAULT   CCDRED    IMAGE   
  	PARAM     KEYWORD   VALUE     VALUE     VALUE   
  	------------------------------------------------------
  	imagetyp  imagetyp            none      ?
  	subset    subset                        ?
  	exptime   exptime             ?         ?
  	darktime  darktime            ?         ?
  	
  	ccdinstrument&gt; imagetyp
  	Image keyword for image type (imagetyp): ccdtype
  	imagetyp  ccdtype             unknown   BIAS
  	ccdinstrument&gt; translate
  	CCDRED image type for 'BIAS' (unknown): zero
  	imagetyp  ccdtype             zero      BIAS
  	ccdinstrument&gt; subset
  	Image keyword for subset parameter (subset): filters
  	subset    filters             1         1 0
  	ccdinstrument&gt; exptime integ
  	exptime   integ               0.        0.
  	ccdinstrument&gt; darktime integ
  	darktime  integ               0.        0.
  	ccdinstrument&gt; show
  	Image: ech001.imh
  	Instrument file: myccd
  	Subset file: subsets
  	
  	CCDRED    IMAGE     DEFAULT   CCDRED    IMAGE   
  	PARAM     KEYWORD   VALUE     VALUE     VALUE   
  	------------------------------------------------------
  	imagetyp  ccdtype             zero      BIAS
  	subset    filters             1         1 0
  	exptime   integ               0.        0.
  	darktime  integ               0.        0.
  	
  	ccdinstrument&gt; next
  	Image: ech002.imh
  	Instrument file: myccd
  	Subset file: subsets
  	
  	CCDRED    IMAGE     DEFAULT   CCDRED    IMAGE   
  	PARAM     KEYWORD   VALUE     VALUE     VALUE   
  	------------------------------------------------------
  	imagetyp  ccdtype             unknown   PROJECTOR FLAT
  	subset    filters             1         1 0
  	exptime   integ               20.       20.
  	darktime  integ               20.       20.
  	
  	ccdinstrument&gt; trans
  	CCDRED image type for 'PROJECTOR FLAT' (unknown): flat
  	imagetyp  ccdtype             flat      PROJECTOR FLAT
  	ccdinstrument&gt; next
  	Image: ech003.imh
  	Instrument file: myccd
  	Subset file: subsets
  	
  	CCDRED    IMAGE     DEFAULT   CCDRED    IMAGE   
  	PARAM     KEYWORD   VALUE     VALUE     VALUE   
  	------------------------------------------------------
  	imagetyp  ccdtype             unknown   COMPARISON
  	subset    filters             1         1 0
  	exptime   integ               300       300
  	darktime  integ               300       300
  	
  	ccdinstrument&gt; translate comp
  	imagetyp  ccdtype             comp      COMPARISON
  	ccdinstrument&gt; next
  	Image: ech004.imh
  	Instrument file: myccd
  	Subset file: subsets
  	
  	CCDRED    IMAGE     DEFAULT   CCDRED    IMAGE   
  	PARAM     KEYWORD   VALUE     VALUE     VALUE   
  	------------------------------------------------------
  	imagetyp  ccdtype             unknown   OBJECT
  	subset    filters             1         1 0
  	exptime   integ               3600      3600
  	darktime  integ               3600      3600
  	
  	ccdinstrument&gt; translate object
  	imagetyp  ccdtype             object    OBJECT
  	ccdinstrument&gt; inst
  	imagetyp                      ccdtype 
  	BIAS                          zero    
  	subset                        filters 
  	exptime                       integ   
  	darktime                      integ   
  	'PROJECTOR FLAT'              flat    
  	COMPARISON                    comp    
  	OBJECT                        object  
  <P>
  	ccdinstrument&gt; next
  	Update instrument file myccd (yes)? 
  </PRE>
  <P>
  3.  Set default geometry parameters.  Note that to set a default the
  arguments must be on the command line.
  <P>
  <PRE>
  	cc&gt; ccdinst ech001 instr=myccd param=common edit+
  	Image: ech001
  	Instrument file: myccd
  	Subset file: subsets
  	
  	CCDRED    IMAGE     DEFAULT   CCDRED    IMAGE   
  	PARAM     KEYWORD   VALUE     VALUE     VALUE   
  	------------------------------------------------------
  	imagetyp  ccdtype             zero      BIAS
  	subset    filters             1         1 0
  	exptime   integ               0.        0.
  	darktime  integ               0.        0.
  	
  	biassec   biassec             ?         ?
  	trimsec   trimsec             ?         ?
  	
  	fixpix    fixpix              no        ?
  	overscan  overscan            no        ?
  	trim      trim                no        ?
  	zerocor   zerocor             no        ?
  	darkcor   darkcor             no        ?
  	flatcor   flatcor             no        ?
  	
  	ccdinstrument&gt; biassec biassec [803:830,*]
  	biassec   biassec   [803:830,*]  [803:830,*]  ?
  	ccdinstrument&gt; trimsec trimsec [2:798,2:798]
  	trimsec   trimsec   [2:798,2:798]  [2:798,2:798]  ?
  	ccdinstrument&gt; instr
  	trimsec                       trimsec  [2:798,2:798]
  	biassec                       biassec  [803:830,*]
  	imagetyp                      ccdtype 
  	BIAS                          zero    
  	subset                        filters 
  	exptime                       integ   
  	darktime                      integ   
  	'PROJECTOR FLAT'              flat    
  	COMPARISON                    comp    
  	OBJECT                        object  
  	
  	ccdinstrument&gt; q
  	Update instrument file myccd (yes)? 
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  instruments, setinstrument
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
