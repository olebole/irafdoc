.. _instruments:

instruments — Instrument specific data files
============================================

**Package: quadred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  instruments -- Instrument specific data files
  </UL>
  <! EndSection:   'NAME'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <B>ccdred</B> package has been designed to accommodate many different
  instruments, detectors, and observatories.  This is done by having
  instrument specific data files.  Note that by instrument we mean a
  combination of detector, instrument, application, and observatory, so
  there might be several "<TT>instruments</TT>" associated with a particular CCD
  detector.  Creating and maintaining the instrument files is generally
  the responsibility of the support staff, though the user may create or
  copy and modify his/her own instrument/application specific files.  The
  task <B>setinstrument</B> makes this information available to the user
  and package easily.
  <P>
  There are three instrument data files, all of which are optional.  The
  package may be used without the instrument files but much of the
  convenience of the package, particularly with respect to using the CCD
  image types, will be lost.  The three files are an instrument image
  header translation file, an initialization task which mainly sets
  default task parameters, and a bad pixel file identifying the cosmic
  bad pixels in the detector.  These files are generally stored in a
  system data directory which is a subdirectory of the logical
  directory "<TT>ccddb$</TT>".  Each file has a root name which identifies the
  instrument.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>1. instrument translation file</H3>
  <! BeginSection: '1. Instrument Translation File'>
  <UL>
  The instrument translation file translates the parameter names used by
  the <B>ccdred</B> pacakge into instrument specific parameters and also
  supplies instrument specific default values.  The package parameter
  <I>ccdred.instrument</I> specifies this file to the package.  The task
  <B>setinstrument</B> sets this parameter, though it can be set
  explicitly like any other parameter.  For the standard instrument
  translation file the root name is the instrument identification and the
  extension is "<TT>dat</TT>" ("<TT>*.dat</TT>" files are protected from being removed in a
  "<TT>stripped</TT>" system, i.e. when all nonessential files are removed).
  Private instrument files may be given any name desired.
  <P>
  The instrument translation proceeds as follows.  When a package task needs
  a parameter for an image, for example "<TT>imagetyp</TT>", it looks in the instrument
  translation file.  If the file is not found or none is specified then the
  image header keyword that is requested has the same name.  If an
  instrument translation file is defined then the requested
  parameter is translated to an image header keyword, provided a translation
  entry is given.  If no translation is given the package name is used.  For
  example the package parameter "<TT>imagetyp</TT>" might be translated to "<TT>data-typ</TT>"
  (the old NOAO CCD keyword).  If the parameter is not found then the default
  value specified in the translation file, if present, is returned.  For recording
  parameter information in the header, such as processing flags, the
  translation is also used.  The default value has no meaning in this case.
  For example, if the flag specifying that the image has been corrected
  by a flat field is to be set then the package parameter name "<TT>flatcor</TT>"
  might be translated to "<TT>ff-flag</TT>".  If no translation is given then the
  new image header parameter is entered as "<TT>flatcor</TT>".
  <P>
  The format of the translation file are lines consisting of the package
  parameter name, followed by the image header keyword, followed by the
  default value.  The first two fields are parameter names.  The fields
  are separated by whitespace (blanks and tabs).  String  default values
  containing blanks must be quoted.  An example is given below.
  <P>
  <PRE>
      # Sample translation file.
      exptime     itime
      darktime    itime
      imagetyp    data-typ
      subset      f1pos
      biassec     biassec    [411:431,2:573]
      datasec     datasec    [14:385,2:573]
  <P>
      fixpix      bp-flag    0
      overscan    bt-flag    0
      zerocor     bi-flag    0
      darkcor     dk-flag    0
      flatcor     ff-flag    0
      fringcor    fr-flag    0 
  </PRE>
  <P>
  The first comment line is ignored as are blank lines.
  The first two lines translate the CCD image type, and the subset parameter
  without default values (see <B>ccdtypes</B> and <B>subsets</B> for more
  information).  The next two lines give the overscan bias strip
  section and the data section with default values for the instrument.
  Note that these parameters may be overridden in the task <B>ccdproc</B>.
  <P>
  The next set of translations requires further discussion.  For processing
  flags the package assumes that the absence of a keyword means that the
  processing has not been done.  If processing is always to be done with
  the <B>CCDRED</B> package and no processing keywords are recorded in the raw data
  then these parameters should be absent (unless you don't like the names
  used by the package).  However, for compatibility with the original NOAO
  CCD images, which may be processed outside of IRAF and which use 0 as the
  no processing value, the processing flags are translated and the false values
  are indicated by the default values.
  <P>
  If there is more than one translation for the same CCDRED parameter,
  for example more than one exptime, then the last one is used.
  <P>
  In addition to the parameter name translations the translation file
  contains translations between the value of the image type parameter
  and the image types used by the package.  These lines
  consist of the image header type string as the first field (with quotes
  if there are blanks) and the image type as recognized by the package.  The
  following example will make this clearer.
  <P>
  <PRE>
  	'OBJECT (0)'		object
  	'DARK (1)'		dark
  	'PROJECTOR FLAT (2)'	flat
  	'SKY FLAT (3)'		other
  	'COMPARISON LAMP (4)'	other
  	'BIAS (5)'		zero
  	'DOME FLAT (6)'		flat
  </PRE>
  <P>
  The values of the image type strings in the header contain blanks so they
  are quoted.  Also the case of the strings is important.  Note that there
  are two types of flat field images and three types of object images.
  <P>
  The CCD image types recognized by the package are:
  <P>
  <PRE>
  	zero   - zero level image such as a bias or preflash
  	dark   - dark count image
  	flat   - flat field image
  	illum  - iillumination image such as a sky image
  	fringe - fringe correction image
  	object - object image
  </PRE>
  <P>
  There may be more than one image type that maps to the same package
  type.  In particular other standard CCD image types, such as comparison
  spectra, multiple exposure, standard star, etc., should be mapped to
  object or other.  There may also be more than one type of flat field,
  i.e. dome flat, sky flat, and lamp flat.  For more on the CCD image
  types see <B>ccdtypes</B>.
  <P>
  The complete set of package parameters are given below.
  The package parameter names are generally the same as the
  standard image header keywords being adopted by NOAO.
  <P>
  <PRE>
  	General Image Header and Default Parameters
      ccdmean		darktime	exptime		fixfile
      imagetyp		ncombine	biassec		subset
      title		datasec         nscanrow
  <P>
  	       CCDRED Processing Flags
      ccdproc		darkcor		fixpix		flatcor
      fringcor		illumcor	overscan	trim
      zerocor
  <P>
  	       CCDRED CCD Image Types
      dark		flat		fringe		illum
      none		object		unknown		zero
  </PRE>
  <P>
  The translation mechanism described here may become more
  sophisticated in the future and a general IRAF system facility may be
  implemented eventually.  For the present the translation mechanism is
  quite simple.
  </UL>
  <! EndSection:   '1. Instrument Translation File'>
  <H3>2. instrument setup script</H3>
  <! BeginSection: '2. Instrument Setup Script'>
  <UL>
  The task <B>setinstrument</B> translates an instrument ID into a
  CL script in the instrument directory.  This script is then executed.
  Generally this script simply sets the task parameters for an
  instrument/application.  However, it could do anything else the support
  staff desires.  Below are the first few lines of a typical instrument setup
  script.
  <P>
  <PRE>
  	ccdred.instrument = "ccddb$kpno/example.dat"
  	ccdred.pixeltype = "real"
  	ccdproc.fixpix = yes
  	ccdproc.overscan = yes
  	ccdproc.trim = yes
  	ccdproc.zerocor = no
  	ccdproc.darkcor = no
  	ccdproc.flatcor = yes
  	ccdproc.biassec = "[411:431,2:573]"
  	ccdproc.datasec = "[14:385,2:573]"
  </PRE>
  <P>
  The instrument parameter should always be set unless there is no
  translation file for the instrument.  The <B>ccdproc</B> parameters
  illustrate setting the appropriate processing flags for the
  instrument.  The overscan bias and trim data sections show an alternate
  method of setting these instrument specific parameters.  They may be
  set in the setup script in which case they are given explicitly in the
  user parameter list for <B>ccdproc</B>.  If the value is "<TT>image</TT>" then
  the parameters may be determined either through the default value in
  the instrument translation file, as illustrated in the previous
  section, or from the image header itself.
  <P>
  The instrument setup script for setting default task parameters may be
  easily created by the support person as follows.  Set the package
  parameters using <B>eparam</B> or with CL statements.  Setting the
  parameters might involve testing.  When satisfied with the way the
  package is set then the parameters may be dumped to a setup script
  using the task <B>dparam</B>.  The final step is editing this script to
  delete unimportant and query parameters.  For example,
  <P>
  <PRE>
  	cl&gt; dparam ccdred &gt;&gt; file.cl
  	cl&gt; dparam ccdproc &gt;&gt; file.cl
  	cl&gt; dparam combine &gt;&gt; file.cl
  		...
  	cl&gt; ed file.cl
  </PRE>
  </UL>
  <! EndSection:   '2. Instrument Setup Script'>
  <H3>3. instrument bad pixel file</H3>
  <! BeginSection: '3. Instrument Bad Pixel File'>
  <UL>
  The bad pixel file describes the bad pixels, columns, and lines in the
  detector which are to be replaced by interpolation when processing the
  images.  This file is clearly detector specific.  The file consists of
  lines describing rectangular regions of the image.
  The regions are specified by four numbers giving the starting and ending
  columns followed by the starting and ending lines.  The starting and
  ending points may be the same to specify a single column or line.  The
  example below illustrates a bad pixel file.
  <P>
  <PRE>
  	# RCA1 CCD untrimmed
  	25 25 1 512
  	108 108 1 512
  	302 302 403 512
  	1 512 70 70
  	245 246 312 315
  </PRE>
  <P>
  If there is a comment line in the file containing the word "<TT>untrimmed</TT>"
  then the coordinates of the bad pixel regions apply to the original CCD
  detector coordinates.
  If the image has been trimmed and the bad pixels are replaced at a later
  stage then this word indicates that the trim region be determined from the
  image header and the necessary coordinate conversion made to the original
  CCD pixel coordinates.  Note that if a subraster readout is used the
  coordinates must still refer to the original CCD coordinates and
  not the raw, untrimmed readout image.  If the word
  "<TT>untrimmed</TT>" does not appear then the coordinates are assumed to apply to
  the image directly; i.e. the trimmed coordinates if the image has been
  trimmed or the original coordinates if the image has not been trimmed.
  The standard bad pixel files should always refer to the original, untrimmed
  coordinates.
  <P>
  The first two bad pixel regions are complete bad columns (the image
  is 512 x 512), the next line is a partial bad column, the next line is
  a bad line, and the last line is a small bad region.  These files are
  easy to create, provided you have a good image to work from and a way
  to measure the positions with an image or graphics display.
  </UL>
  <! EndSection:   '3. Instrument Bad Pixel File'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdtypes, subsets, setinstrument
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'DESCRIPTION' '1. Instrument Translation File' '2. Instrument Setup Script' '3. Instrument Bad Pixel File' 'SEE ALSO'  >
  
