.. _observatory:

observatory — Examine and define observatory parameters
=======================================================

**Package: noao**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  observatory -- Examine and set observatory parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  observatory command obsid [images]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>command = "<TT>list</TT>" (set|list|images)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='command' Line='command = "list" (set|list|images)'>
  <DD>Command option which is one of "<TT>set</TT>", "<TT>list</TT>", or "<TT>images</TT>".  The set command
  sets the default observatory task parameters for the specified
  observatory.  The list command lists the observatory parameters for the
  specified observatory but does not modify the task parameters.  The images
  command lists the observatory parameters for a list of images.  The list
  and images commands examine and verify the observatory parameters applied
  by other tasks using the observatory database facility.
  </DD>
  </DL>
  <DL>
  <DT><B>obsid = "<TT>?</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='obsid' Line='obsid = "?"'>
  <DD>Observatory identification to be set, listed, or used as the default for
  images without the OBSERVAT keyword.  The observatory ID is one of those in
  the database (case ignored), the special string "<TT>observatory</TT>" to default to
  the environment variable "<TT>observatory</TT>" or the <I>observatory.observatory</I>
  parameter, "<TT>obspars</TT>" to select the parameters in the <B>observatory</B>
  task, or "<TT>?</TT>" to list the observatories defined in the database.
  </DD>
  </DL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images to be examined with the "<TT>images</TT>" command.  The images are
  checked for the OBSERVAT keyword to determine the observatory parameters
  to be listed, otherwise the observatory given by <I>obsid</I> is used.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Verbose output?  Because there are a number of different ways in which
  observatory information is determine this option prints detailed
  information on how the observatory database and parameters are
  ultimately selected.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>observatory</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory'>
  <DD>The default observatory used by tasks which use the special
  observatory identification "<TT>observatory</TT>".  The value is one of the
  observatory names in the observatory database (case ignored)
  or the special value "<TT>obspars</TT>" to select the parameters defined in this
  task.  There is no default to force users to set it at least once.
  </DD>
  </DL>
  <DL>
  <DT><B>name</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='name' Line='name'>
  <DD>Observatory name.
  </DD>
  </DL>
  <DL>
  <DT><B>longitude</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='longitude' Line='longitude'>
  <DD>Observatory longitude given in degrees west.
  </DD>
  </DL>
  <DL>
  <DT><B>latitude</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='latitude' Line='latitude'>
  <DD>Observatory latitude in degrees.  Positive latitudes are north and negative
  latitudes are south.
  </DD>
  </DL>
  <DL>
  <DT><B>altitude</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='altitude' Line='altitude'>
  <DD>Observatory altitude in meters above sea level.
  </DD>
  </DL>
  <DL>
  <DT><B>timezone</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='timezone' Line='timezone'>
  <DD>Observatory time zone.  The time zone is the number of hours west of
  Greenwich or the number of hours to be added to local time to obtain
  Greenwich time.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Environment variables</H3>
  <! BeginSection: 'ENVIRONMENT VARIABLES'>
  <UL>
  <DL>
  <DT><B>obsdb</B></DT>
  <! Sec='ENVIRONMENT VARIABLES' Level=0 Label='obsdb' Line='obsdb'>
  <DD>This variable selects the observatory database.  If not defined it defaults
  to noao$lib/obsdb.dat.
  </DD>
  </DL>
  <DL>
  <DT><B>observatory</B></DT>
  <! Sec='ENVIRONMENT VARIABLES' Level=0 Label='observatory' Line='observatory'>
  <DD>This variable selects the observatory entry whenever a task uses the
  observatory name "<TT>observatory</TT>".  If not defined the value of the task
  parameter <I>observatory.observatory</I> is used.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'ENVIRONMENT VARIABLES'>
  <H3>Image header keywords</H3>
  <! BeginSection: 'IMAGE HEADER KEYWORDS'>
  <UL>
  The observatory identification for images is first sought under the
  image header keyword OBSERVAT.  This always takes precedence over any
  other means of defining the observatory.
  </UL>
  <! EndSection:   'IMAGE HEADER KEYWORDS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  OBSERVATORY PARAMETERS IN THE NOAO PACKAGE
  <P>
  Some astronomical data reduction and analysis tasks perform
  computations requiring information about where the data was observed.
  For example a number of <B>noao</B> tasks make corrections for the
  airmass.  Generally they look for an airmass in the image header and
  if it is not present they attempt to compute it from other image header
  parameters.  The information about time and telescope coordinates
  of the observation are often in the image header but the observatory
  latitude is not.  The task must get this information somehow.
  <P>
  Prior to IRAF V2.10 tasks generally had explicit parameters, such as
  latitude, with default values pointing (using parameter redirection) to
  the parameter of the same name in the <B>observatory</B> task.  The
  user was required to know the values of the observatory parameters and
  manually change them for data from different observatories.  In V2.10
  an observatory database has been implemented.  Observatory parameters
  are stored in a simple text file and tasks obtain observatory related
  parameters by specifying an observatory identification.
  <P>
  In general the information about the observatory should be directly
  associated with the image data.  Unless stated otherwise in the
  description of a task,  tasks which require observatory information
  will first look for the image header keyword OBSERVAT.  The value of
  this keyword is the observatory identification used to index the
  observatory database.  The task will then look up any observatory
  parameters it needs in the observatory database.  Data from
  observatories that support this keyword will, therefore, always use the
  correct observatory parameters without user intervention.  All
  observatories which export FITS image data are urged to adopt the
  OBSERVAT keyword (a keyword recommended by the FITS standard).
  <P>
  For image data which do not identify the observatory in this way
  and in tasks which do not operate on images (such as astronomical
  calculator tools), the observatory must be specified by the user.
  Most tasks provide an "<TT>observatory</TT>" parameter which either directly
  selects the observatory or use special values for defining the
  observatory with an environment variable or the parameters
  from the <B>observatory</B> task.
  <P>
  An observatory is specified by the identification name used in the
  observatory database.  The names in the database may be listed using
  the <B>observatory</B> task as described below.  If the desired observatory
  is not in the database a user may copy/create their own database and
  select it with the environment variable "<TT>obsdb</TT>", modify the standard
  database if allowed (any changes to the distributed version should
  be forwarded to iraf$noao.edu), or use the special observatory name
  "<TT>obspars</TT>".  The last option directly uses the parameters in the
  <B>observatory</B> task which can be set to any values using the normal
  parameter editing mechanism.
  <P>
  The default value for the observatory parameter in a task is generally
  "<TT>observatory</TT>".  This special name directs the task to look first
  for the environment variable of the same name and then at the
  <I>observatory</I> parameter of the <B>observatory</B> task.  The environment
  variable allows users or sites to set the default observatory in their
  login files and site defaults.  Also it is simple to change the
  default observatory either with a <B>reset</B> command or the
  <B>observatory</B> command.
  <P>
  The observatory database is selected by the environment variable
  "<TT>obsdb</TT>".  The default when the variable is not defined is the
  <B>noao</B> package library database file "<TT>noao$lib/obsdb.dat</TT>".  The use
  of an environment variable allows users to permanently change the
  default database in the OS environment (when IRAF has access to it such
  as in UNIX systems) or in the startup IRAF environment as set in the
  "<TT>login.cl</TT>" or "<TT>loginuser.cl</TT>" files.  One can, of course, change it
  during a session with the set or reset commands.  For sites which want
  to customize the observatory mechanism the environment variables can
  also be set and changed in the files "<TT>hlib$zzsetenv.def</TT>",
  "<TT>noao$lib/zzsetenv.def</TT>", and the template login file "<TT>hlib$login.cl</TT>".
  <P>
  An observatory database file consist of a simple list of keyword=value
  pairs with arbitrary whitespace allowed.  An observatory entry begins
  with the observatory keyword and extends to the next observatory
  keyword or the end of the file.  The observatory identification should
  be the same as the string used in the OBSERVAT image header parameter
  for data from that observatory.  The default file noao$lib/obsdb.dat
  begins as follows:
  <P>
  <PRE>
  # Observatory Parameters.  Taken from the Almanac.
  #
  # Observatories wishing to be added or make changes in the default
  # distributed database should send information to iraf@noao.edu.
  <P>
  observatory = "kpno"
  	name = "Kitt Peak National Observatory"
  	longitude = 111:36.0
  	latitude = 31:58.8
  	altitude = 2120.
  	timezone = 7
  <P>
  observatory = "ctio"
  	&lt;etc&gt;
  </PRE>
  <P>
  In summary, access to observatory parameters is now done by referencing
  the image header keyword OBSERVAT and, if not defined, determine the
  observatory name from a task parameter.  The environment variables
  "<TT>observatory</TT>" and "<TT>obsdb</TT>" can be set by the user to select alternate
  observatories and observatory database files.  For data without an
  observatory entry the observatory can be set to "<TT>obspars</TT>" or the user
  may make their own observatory database.
  <P>
  THE OBSERVATORY TASK
  <P>
  The <B>observatory</B> task serves a number of functions.  It may be used to
  examine the observatory database, verify the observatory parameters which
  will be used by other tasks, particularly those operating on images, set
  the default observatory if not defined by other means, set observatory
  parameters explicitly, especially when there is no observatory database
  entry, and as a parameter set for tasks which explicitly reference
  observatory parameters.  The <B>verbose</B> parameter also provides a
  detailed check of the steps used to determine the observatory database,
  observatory identification, and observatory parameters.
  <P>
  The <I>command</I> parameter takes the values "<TT>set</TT>", "<TT>list</TT>", or "<TT>images</TT>".
  The <I>obsid</I> parameter supplies the observatory identification and the
  <I>images</I> parameter is used to specify a list of images for the "<TT>images</TT>"
  command.  The parameters are query parameters and so may be either queried
  or simply typed on the command line.
  <P>
  The "<TT>set</TT>" command prints the observatory parameters for the specified
  observatory and sets many of these in the <B>observatory</B> task
  parameters.  This command is used to set the default observatory parameters
  for tasks where images are not used, the images do not contain the
  observatory id, or direct references to specific parameters with parameter
  redirection (for example "<TT>)observatory.latitude</TT>") are used.
  <P>
  The "<TT>list</TT>" command is similar to the "<TT>set</TT>" command except the task parameters
  are not modified.  It is used to list observatory parameters.  It is also
  use with the special observatory identifications to list the entries in
  an observatory database and verify the observatory to be used by
  tasks which do not operate on images.  The special value "<TT>?</TT>" lists
  the entries in the database.  The special value "<TT>observatory</TT>" lists
  the observatory defined by the "<TT>observatory</TT>" environment variable or
  that given by the <I>observatory.observatory</I> parameter.  The special
  value "<TT>obspars</TT>" simply lists the observatory task parameters.
  <P>
  The "<TT>images</TT>" command lists the observatory information applicable to
  one or more images.  In particular, the observatory identification is
  first sought in OBSERVAT image header keyword and, if not found, the
  <I>obsid</I> parameter is used.  Often the default observatory is
  "<TT>observatory</TT>" to follow the same search path used by other tasks.
  <P>
  The <I>verbose</I> parameter prints additional detailed information.  It
  prints the database used and whether it is selected by default
  (noao$lib/obsdb.dat) or by the "<TT>obsdb</TT>" environment variable.  When the
  observatory is defined as "<TT>observatory</TT>" it indicates whether the
  observatory is defined by the environment variable "<TT>observatory</TT>" or by the
  observatory task.  When listing images it prints the OBSERVAT keyword or
  the default observatory assigned.
  <P>
  For observatories not in a database the name, latitude, longitude,
  altitude, and time zone parameters may be set using <B>eparam</B>.
  The observatory id must be set to "<TT>obspars</TT>" in this case.
  These parameters will then be referenced by other tasks in which
  the observatory is specified as "<TT>obspars</TT>".  This allows arbitrary
  observatory parameters to be set without creating or modifying
  an observatory database.  However, it is advisable to create a
  local database and also send the observatory information to the
  IRAF group at NOAO for inclusion in the default database.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  List the observatory entries in the database:
  <P>
  <PRE>
  	cl&gt; observatory list ? v+
  	Using default observatory database: noao$lib/obsdb.dat
  <P>
  	default: Kitt Peak National Observatory
  	kpno: Kitt Peak National Observatory
  	ctio: Cerro Tololo Interamerican Observatory
  	eso: European Southern Observatory
  	lick: Lick Observatory
  	mmt: Whipple Observatory
  	cfht: Canada-France-Hawaii Telescope
  	lapalma: Roque de los Mucachos, La Palma
  </PRE>
  <P>
  2.  Set the observatory parameters for Cerro Tololo:
  <P>
  <PRE>
  	cl&gt; observatory set ctio
  	Observatory parameters for Cerro Tololo...
  		observatory = ctio
  		timezone = 5
  		altitude = 2215.
  		latitude = -30:09.9
  		longitude = 70:48.9
  	         name = 'Cerro Tololo Interamerican Observatory'
  	cl&gt; lpar observatory
  	      command = "set"		Command (set|list|images)
  	     argument = ctio		Observatory or images
  	 (observatory = "ctio")         Observatory identification
  	        (name = "Cerro Tololo...") Observatory name
  	   (longitude = 70.815)         Observatory longitude (degrees)
  	    (latitude = -30.165)        Observatory latitude (degrees)
  	    (altitude = 2215.)          Observatory altitude (meters)
  	    (timezone = 4)              Observatory time zone
  	     (verbose = no)             Verbose output?
  	        (mode = "q")            
  </PRE>
  <P>
  3.  Set the observatory parameters to use the environment variable
  "<TT>observatory</TT>" and verify it.
  <P>
  <PRE>
  	cl&gt; set observatory=cfht
  	cl&gt; observatory list observatory
  	Observatory parameters for Canada-France-Hawaii Telescope
  		observatory = cfht
  		timezone = 10
  		altitude = 4215
  		latitude = 19:49.6
  		longitude = 155:28.3
  		name = 'Canada-France-Hawaii Telescope'
  </PRE>
  <P>
  4.  Change the default observatory database and verify verbosely:
  <P>
  <PRE>
  	cl&gt; set observatory="sco"
  	cl&gt; set obsdb="/local/iraf/obsdb.dat"
  	cl&gt; type obsdb$
  	# Local Observatory Parameters.
  <P>
  	observatory = "sco"
  		name = "Small College Observatory"
  		longitude = 100:20.0
  		latitude = 35:58.8
  		altitude = 212.
  		timezone = 6
  	cl&gt; observ set observatory v+
  	Using database defined by 'obsdb' environment variable:
  		/tmp/test/obsdb.dat
  	Using obs... defined by 'obs...' environment variable: sco
  	Using observatory parameters for database entry: sco
  	Observatory parameters for Small College Observatory
  		observatory = sco
  		timezone = 6
  		altitude = 212.
  		latitude = 35:58.8
  		longitude = 100:20.0
  		name = 'Small College Observatory'
  </PRE>
  <P>
  5.  List the observatory assigned to some images with a default observatory
  determined either by the "<TT>observatory</TT>" environment variable or that set
  in the observatory task.
  <P>
  <PRE>
  	cl&gt; observ images observatory dev$pix,demoobj1
  	Observatory parameters for Small College Observatory
  		observatory = sco
  		timezone = 6
  		altitude = 212.
  		latitude = 35:58.8
  		longitude = 100:20.0
  		name = 'Small College Observatory'
  		Images: dev$pix (default observatory)
  	Observatory parameters for Kitt Peak National Observatory
  		observatory = kpno
  		timezone = 7
  		altitude = 2120.
  		latitude = 31:58.8
  		longitude = 111:36.0
  		name = 'Kitt Peak National Observatory'
  		Images: demoobj1 (OBSERVAT keyword)
  <P>
  </PRE>
  <P>
  6.  Set explicit observatory parameters:
  <P>
  <PRE>
  	cl&gt; epar observatory
  	&lt;set observatory parameters&gt;
  	cl&gt; observ list obspars
  	Observatory parameters for North Pole
  		observatory = obspars
  		timezone = 0
  		altitude = 0.
  		latitude = 90.
  		longitude = 0.
  		name = 'North Pole'
  </PRE>
  <P>
  7.  Use observatory parameters in expressions:
  <P>
  <PRE>
  	cl&gt; observ set kpno
  	Observatory parameters for Kitt Peak National Observatory
  		observatory = kpno
  		timezone = 7
  		altitude = 2120.
  		latitude = 31:58.8
  		longitude = 111:36.0
  		name = 'Kitt Peak National Observatory'
  	cl&gt; = observ.lat
  	31.98
  	cl&gt; = sin (3.14159/180 * observ.lat)
  	0.52962280742153
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  Tasks in astutil, imred, onedspec, and twodspec.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ENVIRONMENT VARIABLES' 'IMAGE HEADER KEYWORDS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
