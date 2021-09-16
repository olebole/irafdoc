.. _rvidlines:

rvidlines — Measure radial velocities from spectral lines
=========================================================

**Package: rv**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rvidlines -- Measure radial velocities from spectral lines
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rvidlines images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of spectral images in which to identify spectral lines and measure a
  velocity.  The spectra must be dispersion calibrated in Angstroms.
  </DD>
  </DL>
  <DL>
  <DT><B>section = "<TT>middle line</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = "middle line"'>
  <DD>If an image is not one dimensional or given as a one dimensional image
  section then the image section given by this parameter is used.  The
  section is used to define the initial vector and the direction (columns,
  lines, or "<TT>z</TT>") of the image vectors to be fit.  The image is still considered
  to be two or three dimensional and it is possible to change the data vector
  within the program.
  <P>
  The section parameter may be specified directly as an image section or
  in one of the following forms
  <P>
  <PRE>
  line|column|x|y|z first|middle|last|# [first|middle|last|#]]
  first|middle|last|# [first|middle|last|#] line|column|x|y|z
  </PRE>
  <P>
  where each field can be one of the strings separated by | except for #
  which is an integer number.  The field in [] is a second designator
  which is used with 3D data.  See the example section for examples of
  this syntax.  Abbreviations are allowed though beware
  that <TT>'l'</TT> is not a sufficient abbreviation.
  </DD>
  </DL>
  <DL>
  <DT><B>database = "<TT>database</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "database"'>
  <DD>Database in which the feature data and redshifts are recorded.
  </DD>
  </DL>
  <DL>
  <DT><B>coordlist = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coordlist' Line='coordlist = ""'>
  <DD>User coordinate list consisting of an ordered list of rest spectral line
  coordinates.  If a line list is defined lines from the list may be
  automatically found and added to the lines being measured.
  </DD>
  </DL>
  <DL>
  <DT><B>nsum = "<TT>10</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nsum' Line='nsum = "10"'>
  <DD>Number of lines, columns, or bands across the designated vector axis to be
  summed when the image is a two or three dimensional spatial spectrum.
  It does not apply to multispec format spectra.  If the image is three
  dimensional an optional second number can be specified for the higher
  dimensional axis  (the first number applies to the lower axis number and
  the second to the higher axis number).  If a second number is not specified
  the first number is used for both axes.
  </DD>
  </DL>
  <DL>
  <DT><B>match = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='match' Line='match = 5.'>
  <DD>The maximum difference for a match between the measured line coordinate
  and a coordinate in the coordinate list.  The units of this parameter
  is that of the user coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>maxfeatures = 50</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxfeatures' Line='maxfeatures = 50'>
  <DD>Maximum number of the strongest features to be selected automatically from
  the coordinate list (function <TT>'l'</TT>) or from the image data (function <TT>'y'</TT>).
  </DD>
  </DL>
  <DL>
  <DT><B>zwidth = 100.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='zwidth' Line='zwidth = 100.'>
  <DD>Width of graphs, in user coordinates, when in zoom mode (function <TT>'z'</TT>).
  </DD>
  </DL>
  <P>
  The following parameters are used in determining feature positions.
  <DL>
  <DT><B>ftype = "<TT>absorption</TT>" (emission|absorption|gemission|gabsorption)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ftype' Line='ftype = "absorption" (emission|absorption|gemission|gabsorption)'>
  <DD>Type of features to be identified.  The possibly abbreviated choices are
  "<TT>emission</TT>", "<TT>absorption</TT>", "<TT>gemission</TT>", and "<TT>gabsorption</TT>".  The first two
  select the <B>center1d</B> centering algorithm while the last two
  select the Gaussian fitting centering algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B>fwidth = 4.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fwidth' Line='fwidth = 4.'>
  <DD>Width in pixels of features to be identified.
  </DD>
  </DL>
  <DL>
  <DT><B>cradius = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cradius' Line='cradius = 5.'>
  <DD>The maximum distance, in pixels, allowed between a feature position
  and the initial estimate when defining a new feature.
  </DD>
  </DL>
  <DL>
  <DT><B>threshold = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 0.'>
  <DD>In order for a feature center to be determined the range of pixel intensities
  around the feature must exceed this threshold.
  </DD>
  </DL>
  <DL>
  <DT><B>minsep = 2.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minsep' Line='minsep = 2.'>
  <DD>The minimum separation, in pixels, allowed between feature positions
  when defining a new feature.
  </DD>
  </DL>
  <P>
  The following parameters control the input and output.
  <DL>
  <DT><B>logfile = "<TT>logfile</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "logfile"'>
  <DD>Log file for recording the results of the velocity measurements.  The
  results are written when exiting or changing input images.  The
  results can be previewed with the "<TT>:features</TT>" command.  If no log file
  is specified then the results are not saved.
  </DD>
  </DL>
  <DL>
  <DT><B>autowrite = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='autowrite' Line='autowrite = no'>
  <DD>Automatically write or update the logfile and database?  If no then a query
  is given for writing results to the logfile.  A query for writing to the
  database is also given if the feature data have been modified.  If yes
  exiting the program automatically writes to the logfile and updates the
  database.
  </DD>
  </DL>
  <DL>
  <DT><B>keywpars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keywpars' Line='keywpars = ""'>
  <DD>The image header keyword translation table as described in 
  the <I>keywpars</I> named pset.  This defines the header keywords used
  to obtain the observation information needed for computing the
  heliocentric velocity.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Graphics device.  The default is the standard graphics device which is
  generally a graphics terminal.
  </DD>
  </DL>
  <DL>
  <DT><B>cursor = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Cursor input file.  If a cursor file is not given then the standard graphics
  cursor is read.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Addtional parameters</H3>
  <! BeginSection: 'ADDTIONAL PARAMETERS'>
  <UL>
  The measured velocities are corrected to a heliocentric frame of reference
  if possible.  This requires determining various parameters about the
  observation.  The latitude, longitude, and altitude of the observation
  are determined from the observatory database.  The observatory is
  defined by either the OBSERVAT image header keyword or the "<TT>observatory</TT>"
  package parameter in that order.  See the help for <B>observatory</B>
  for additional information.
  <P>
  The date, universal time, right ascension, declination, and coordinate epoch
  for the observation are obtained from the image header.  The keywords
  for these parameters are defined in the <B>keywpars</B> parameter set.
  Note that the parameters used are "<TT>ra</TT>", "<TT>dec</TT>", "<TT>ut</TT>", and "<TT>date-obs</TT>".
  The "<TT>utmiddle</TT>" parameter is not used so if you have a keyword for the
  middle of the exposure that you want to use then you must set the
  "<TT>ut</TT>" parameter to reference that keyword.
  <P>
  Before IRAF V2.12, if the date keyword included a time then that time was
  used and the "<TT>ut</TT>" keyword was not used.  In V2.12 this was changed and the
  time is always taken from the keyword specified by "<TT>ut</TT>".  However, the
  value can be in either a single time or a date/time string.  So if you
  want to use both the date and time from the same keyword, say DATE-OBS,
  then point the "<TT>date_obs</TT>" and "<TT>ut</TT>" parameters in KEYWPARS to the same
  keyword.
  </UL>
  <! EndSection:   'ADDTIONAL PARAMETERS'>
  <H3>Cursor keys</H3>
  <! BeginSection: 'CURSOR KEYS'>
  <UL>
  <P>
  <PRE>
  ?  Clear the screen and print menu of options
  a  Apply next (c)enter or (d)elete operation to (a)ll features
  b  Mark and de(b)lend features by Gaussian fitting
  c  (C)enter the feature nearest the cursor
  d  (D)elete the  feature nearest the cursor
  f  (F)it redshift and velocity from the fitted and user coordinates
  i  (I)nitialize (delete features and coordinate fit)
  j  Go to the preceding image line/column/band/aperture
  k  Go to the next image line/column/band/aperture
  l  Match coordinates in the coordinate (l)ist
  m  (M)ark new feature near the cursor and enter coord and label
  n  Move the cursor or zoom to the (n)ext feature (same as +)
  o  Go to the specified image line/column/band/aperture
  p  (P)an to user defined window after (z)ooming on a feature
  q  (Q)uit and continue with next image (also carriage return)
  r  (R)edraw the graph
  t  Reset the position of a feature without centering
  u  Enter a new (u)ser coordinate and label for the current feature
  w  (W)indow the graph.  Use <TT>'?'</TT> to window prompt for more help.
  y  Automatically find strongest peaks and identify them
  z  (Z)oom on the feature nearest the cursor
  +  Move the cursor or zoom to the next feature
  -  Move the cursor or zoom to the previous feature
  I  Interrupt task and exit immediately
  </PRE>
  <P>
  The parameters are listed or set with the following commands which may be
  abbreviated.  To list the value of a parameter type the command alone.
  <P>
  <PRE>
  :show file		Show the values of all the parameters
  :features file		Write feature list to file (default STDOUT)
  <P>
  :coordlist file		Coordinate list file
  :cradius value		Centering radius in pixels
  :threshold value	Detection threshold for feature centering
  :database name		Database for recording feature records
  :ftype value		Feature type
  			  (emission|absorption|gemission|gabsorption)
  :fwidth value		Feature width in pixels
  :image imagename 	Set a new image or show the current image
  :labels value		Feature label type
  			    (none|index|pixel|coords|user|both)
  :match value		Coordinate list matching distance
  :maxfeatures value	Maximum number of features automatically found
  :minsep value		Minimum separation allowed between features
  :read name ap		Read a record from the database
  			  (name/ap default to the current spectrum)
  :write name ap		Write a record to the database
  			  (name/ap default to the current spectrum)
  :add name ap		Add features from the database
  			  (name/ap default to the current spectrum)
  :zwidth value		Zoom width in user units
  <P>
  Labels:
        none - No labels
       index - Sequential numbers in increasing pixel position
       pixel - Pixel coordinates
      coords - User coordinates such as wavelength
        user - User labels
        both - Combination of coords and user
  </PRE>
  </UL>
  <! EndSection:   'CURSOR KEYS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Rvidlines</B> measures radial velocities from spectra by determining the
  wavelength shift in spectral lines relative to specified rest wavelengths.
  The basic usage consists of identifying one or more spectral lines (also
  called features), entering the rest wavelengths, and computing the average
  wavelength shift converted to a radial velocity.  Additional lines can then
  be automatically added from a coordinate list of rest wavelengths.
  <P>
  Each dispersion calibrated image in the input list is examined in turn.  If
  the image is not one dimensional or a one dimensional section of an image
  then the image section given by the parameter <I>section</I> is used.  This
  parameter may be specified in several ways as described in the parameter
  and examples sections.  The image section is used to select a starting
  vector and image axis.  The parameter <I>nsum</I> determines the number
  of lines, columns, or bands to sum in a two or three dimensional image.
  <P>
  Once a spectrum has been selected it is graphed.  The graph title includes
  the image name, spectrum title, and the current velocity and redshift if
  one has been determined.  An initial feature list is read from the database
  if an entry exists.  The features are marked on the graph by tick marks.
  The features may also be labeled using the "<TT>:label</TT>" option.  The graph has
  the observed wavelength scale along the bottom and the rest wavelength
  scale along the top (if a velocity has been determined).  The status line
  gives the pixel coordinate, observed wavelength, rest wavelength (as
  computed by the last velocity computation), the true rest wavelength, the
  velocity residual, and an optional identification string for the "<TT>current</TT>"
  feature.
  <P>
  The graphics cursor is used to select features and perform various
  functions.  A menu of the keystroke options and functions is printed with
  the key <TT>'?'</TT>.  The cursor keys and their functions are defined in the CURSOR
  KEYS section and described further below.  The standard cursor mode keys
  are also available to window and redraw the graph and to produce hardcopy
  "<TT>snaps</TT>".
  <P>
  There are two types of feature selection functions;  defining new
  features and selecting previously defined features.  The <TT>'m'</TT> key marks
  a new feature near the cursor position.  The feature position is
  determined by a centering algorithm.  There are two algorithms;
  a flux bisecting algorithm called <B>center1d</B> and a gaussian
  profile fitting algorithm.  The choice of fitting algorithm and whether the
  feature is an emission or absorption line is set by the <I>ftype</I>
  parameter.
  <P>
  The center1d algorithm is described in the help topic <B>center1d</B>.  The
  parameters which control it are <I>fwidth</I>, <I>ftype</I>, <I>cradius</I>,
  and <I>threshold</I>.
  <P>
  The gaussian fitting algorithm estimates a linear local background by
  looking for the minimum or maximum, depending on whether the feature type
  is set to absorption or emission, within a distance of the entered cursor
  position of one-half the feature width specified by the <I>fwidth</I>
  parameter plus the centering error radius specified by the <I>cradius</I>
  parameters.  This background estimation is crude but generally is not
  critical for reasonably strong lines.  Once the sloped background is
  defined a non-linear Levenberg-Marquardt algorithm determines the gaussian
  center, peak strength, and sigma.  The initial estimates for these
  parameters are the starting center, the background subtracted pixel value
  at the starting center, and the <I>fwidth</I> value divided by six.  After
  fitting the gaussian model it is overplotted on the data for comparison.  The
  <I>threshold</I> parameter also applies to this algorithm to check for a
  minimum data range and the <I>cradius</I> parameter checks for a maximum
  error in the center from the initial value.
  <P>
  For a more critical setting of the background in the gaussian algorithm or
  for the simultaneous solution of multiple gaussian components (deblending)
  the <TT>'b'</TT> key is available.  The <TT>'b'</TT> key is used to mark the initial
  positions of up to ten features.  The feature marking ends with <TT>'q'</TT>.  The
  user is then queried to mark two points for the linear background.  After
  doing the simultaneous fitting the user is queried sequentially for the
  rest wavelengths of each line.  Note that the <TT>'b'</TT> key will do the gaussian
  fitting regardless of whether the <I>ftype</I> setting is for a gaussian
  or not and can be used for fitting just a single line.
  <P>
  When a feature is defined the value of <I>ftype</I> and <I>fwidth</I> are
  associated with the feature.  Subsequent recentering will use these values
  even if the default values are changed.  This is how a combination of
  absorption and emission lines may be defined.  The only constraint to this
  is that the feature data does not record the combination of lines used in a
  deblending operation so automatic recentering will treat each line
  separately.
  <P>
  When a new feature is marked if the wavelength is within a distance given
  by the parameter <I>minsep</I> of a previous feature it is considered to be
  the same feature and replaces the old feature.  The coordinate list is
  searched for a match between the measured wavelength, corrected to rest
  using the current velocity, and a user coordinate in the list.  The
  matching is based on the nearest line within a specified <I>match</I>
  distance.  If a match is found it becomes the default user coordinate which
  the user may override.  The new feature is marked on the graph and it
  becomes the current feature.  The redefinition of a feature which is within
  the minimum separation may be used to set the user coordinate from the
  coordinate list.  The <TT>'t'</TT> key allows setting the position of a feature to
  other than that found by the centering algorithms.
  <P>
  If at least one feature is marked with it's rest wavelength specified then
  the <TT>'l'</TT> key may be used to identify additional features from a coordinate
  list of rest wavelengths.  First a velocity is computed from the initial
  features.  Then each coordinate in the list is corrected to the
  observed velocity and a feature is sought in the data at that point.
  Up to a maximum number of features, set by the parameter <I>maxfeatures</I>,
  may be defined in this way.  A new velocity is computed using all the
  located features.
  <P>
  The <TT>'y'</TT> key provides another way to add features.  Rather than look for
  features at the coordinates of a list, a peak finding algorithm is used to
  find features up to the specified maximum number.  If there are more
  peaks only the strongest are kept.  The peaks are then matched against the
  coordinate list to find user coordinate values.
  <P>
  To select a different feature as the current feature the keys <TT>'.'</TT>, <TT>'n'</TT>,
  <TT>'+'</TT>, and <TT>'-'</TT> are used.  The <TT>'.'</TT> selects the feature nearest the cursor, the
  <TT>'n'</TT> and <TT>'+'</TT> select the next feature, and the <TT>'-'</TT> selects the previous
  feature relative to the current feature in the feature list as ordered by
  pixel coordinate.  These keys are useful when redefining the user
  coordinate with the <TT>'u'</TT> key and when examining features in zoom mode.
  <P>
  The key <TT>'f'</TT> computes ("<TT>fits</TT>") a velocity to the defined features.
  This is done by taking a weighted average of the redshifts,
  <P>
  <PRE>
  	z = (measured - true) / true
  </PRE>
  <P>
  of the individual lines.  The default weights are always one but a different
  weight may be entered with the <TT>'u'</TT> key.  The average redshift is
  converted to a Cz velocity (redshift times the speed of light) and
  corrected to a heliocentric frame if possible.
  <P>
  The heliocentric correction requires observatory and observation information.
  The observatory is determined either from the OBSERVAT keyword in the
  image header or by the "<TT>rv.observatory</TT>" package parameter.  For a
  discussion of how an observatory is defined and used see the help
  for <B>observatory</B>.  In addition to the observatory the right
  ascension, declination, coordinate epoch, and date and time of the
  observation are required.  If the time is in the date string it has
  precedence over the time keyword.  This information is sought in the image
  header using the keywords defined in the <B>keywpars</B> parameter
  file.  If there is insufficient information for the heliocentric
  velocity correction only the observed velocity will be given.  The
  type of velocity (both velocity and redshift) is indicated by
  identifiers such as Vobs and Vhelio.
  <P>
  Note that a new velocity is only computed after typing <TT>'f'</TT>, <TT>'l'</TT>,
  "<TT>:features</TT>", or when exiting and writing the results to the database.
  In other words, adding new features or deleting existing features
  does not automatically update the velocity determination.
  <P>
  Features may be deleted with the key <TT>'d'</TT>.  All features are deleted
  when the <TT>'a'</TT> key immediately precedes the delete key.  Deleting the
  features does not reset the velocity.  The <TT>'i'</TT> key initializes
  everything by removing all features and reseting the velocity.
  <P>
  It is common to transfer the feature identifications and velocities
  from one image to another.  When a new image without a database entry
  is examined, such as when going to the next image in the input list,
  changing image lines or columns with <TT>'j'</TT>, <TT>'k'</TT> and <TT>'o'</TT>, or selecting
  a new image with the "<TT>:image</TT>" command, the current feature list and
  velocity are kept.  Alternatively, a database record from a different
  image may be read with the "<TT>:read</TT>" command.  When transferring feature
  identifications between images the feature coordinates will not agree exactly
  with the new image feature positions and several options are available to
  reregister the feature positions.  The key <TT>'c'</TT> centers the feature nearest
  the cursor using the current position as the starting point.  When preceded
  with the <TT>'a'</TT> key all the features are recentered (the user must refit
  the coordinate function if desired).  As an aside, the recentering
  function is also useful when the parameters governing the feature
  centering algorithm are changed.  An additional options is the "<TT>:add</TT>"
  command to add features from a database record.  This does not overwrite
  previous features as does "<TT>:read</TT>".
  <P>
  Note that when a set of spectra all have the same features in nearly
  the same location the task <B>rvreidlines</B> may be used to reidentify
  the lines and compute a new velocity.
  <P>
  In addition to the single keystroke commands there are commands initiated
  by the key <TT>':'</TT> (colon commands).  As with the keystroke commands there are
  a number of standard graphics features available beginning with "<TT>:.</TT>" (type
  "<TT>:.help</TT>" for these commands).  The rvidlines colon commands allow the task
  parameter values to be listed and to be reset within the task.  A parameter
  is listed by typing its name.  The colon command "<TT>:show</TT>" lists all the
  parameters.  A parameter value is reset by typing the parameter name
  followed by the new value; for example "<TT>:match 10</TT>".  Other colon commands
  display the feature list and velocities (:features), control reading and
  writing records to the database (:read and :write), and set the graph
  display format.
  <P>
  The feature identification process for an image is completed by typing <TT>'q'</TT>
  to quit.  Attempting to quit an image without explicitly logging the
  results or recording changes in the feature database produces a warning
  message unless the <I>autowrite</I> parameter is set.  If this parameter is
  not set prompts are given asking whether to save the results to the log
  file and the database, otherwise the results are automatically saved.  As
  an immediate exit the <TT>'I'</TT> interrupt key may be used.  This does not save
  the feature information and may leave the graphics in a confused state.
  <P>
  The information recorded in the logfile, if one is specified, includes
  information about the observatory used for heliocentric corrections
  (to verify the correct observatory was used), the list of features
  used in the velocity computation, the wavelength and velocity RMS,
  and lines with the observed and heliocentric redshifts and velocities.
  These lines include an error in the mean derived from the weighted
  RMS and the number of lines used, and the number of lines.  This output
  format is designed so that if there are multiple velocities recorded
  in the same log file they can be easily extracted with the match command:
  <P>
  <PRE>
      cl&gt; match Vhelio logfile
      im1 45 : Vhelio = 15.06 km/s, Mean err = 4.593 km/s, Lines = 7
      im1 40 : Vhelio = 17.77 km/s, Mean err = 3.565 km/s, Lines = 7
      im2 45 : Vhelio = 24.44 km/s, Mean err = 3.741 km/s, Lines = 7
      im2 40 : Vhelio = 14.65 km/s, Mean err =  11.2 km/s, Lines = 7
      ...
  </PRE>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Database records</H3>
  <! BeginSection: 'DATABASE RECORDS'>
  <UL>
  The database specified by the parameter <I>database</I> is a directory of
  simple text files.  The text files have names beginning with 'id' followed
  by the entry name, usually the name of the image.  The database text files
  consist of a number of records.  A record begins with a line starting with the
  keyword "<TT>begin</TT>".  The rest of the line is the record identifier.  Records
  read and written by <B>rvidlines</B> have "<TT>identify</TT>" as the first word of the
  identifier.  Following this is a name which may be specified following the
  "<TT>:read</TT>" or "<TT>:write</TT>" commands.  If no name is specified then the image name
  is used.  For 1D spectra the database entry includes the aperture number
  and so to read a solution from a aperture different than the current image
  and aperture number must be specified.  For 2D/3D images the entry name
  has the 1D image section which is what is specified to read the entry.
  The lines following the record identifier contain
  the feature information and redshift (without heliocentric correction).
  <P>
  The database files have the name "<TT>identify</TT>" and the prefix "<TT>id</TT>" because
  these files may also be read by the <B>identify</B> task for changing
  the dispersion function based on the rest wavelengths.
  </UL>
  <! EndSection:   'DATABASE RECORDS'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  The radial velocity of the  spectrum, kstar1, is to be determined.
  The user creates a list of line features to be used in the file
  klines.dat.
  <P>
  <PRE>
      cl&gt; rvidlines kstar1 coord=klines.dat
  	a. The spectrum is drawn
  	b. A line is marked with <TT>'m'</TT>
  	c. Enter the rest wavelength
  	d. Compute a velocity with <TT>'f'</TT>
  	e. Find other lines in the list with <TT>'l'</TT>
  	f. Exit with <TT>'q'</TT>
      Write velocity data to the logfile (yes)? y
      Write feature data to the database (yes)? y
      cl&gt; match Vhelio logfile
      kstar1 1 : Vhelio = 25.1 km/s, Mean err = 1.123 km/s, Lines = 10
  </PRE>
  <P>
  2.  For echelle or multispec spectra the keys <TT>'o'</TT>, <TT>'j'</TT>, and <TT>'k'</TT> may
  be used to switch between spectra.  Note that the inheritance of features
  in echelle orders is not very useful.  So the <TT>'i'</TT> can be used to
  initialize.  For similar spectra the <TT>'a'</TT><TT>'c'</TT> key combination may
  be used to recenter all lines and the a new <TT>'f'</TT> fit can be done.
  <P>
  3.  For images which are two or three dimensional it is necessary to
  specify the image axis for the data vector and the number of pixels at each
  point across the vector direction to sum.  One way specify a vector is to
  use an image section to define a vector.  For example, to select column
  20:
  <P>
  <PRE>
      cl&gt; rvidlines obj[20,*]
  </PRE>
  <P>
  The alternative is to use the section parameter.  Below are some examples
  of the section parameter syntax for an image "<TT>im2d</TT>" which is 100x200
  and "<TT>im3d</TT>" which is 100x200x50.  On the left is the section string syntax
  and on the right is the image section
  <P>
  <PRE>
      Section parameter |  Image section      |  Description
      ------------------|---------------------|---------------------
      first line        |  im2d[*,1]          |  First image line
      middle column     |  im2d[50,*]         |  Middle image column
      last z            |  im3d[100,200,*]    |  Last image z vector
      middle last y     |  im3d[50,*,50]      |  Image y vector
      line 20           |  im2d[*,20]         |  Line 20
      column 20         |  im2d[20,*]         |  Column 20
      x 20              |  im2d[*,20]         |  Line 20
      y 20              |  im2d[20,*]         |  Column 20
      y 20 30           |  im2d[20,*,30]      |  Column 20
      z 20 30	      |  im3d[20,30,*]      |  Image z vector
      x middle          |  im3d[*,100,25]     |  Middle of image
      y middle          |  im3d[50,*,25]      |  Middle of image
      z middle          |  im3d[50,100,*]     |  Middle of image
  </PRE>
  <P>
  The most common usage should be "<TT>middle line</TT>", "<TT>middle column</TT>" or "<TT>middle z</TT>".
  <P>
  The summing factors apply to the axes across the specified vector.  For
  3D images there may be one or two values.  The following shows which axes
  are summed, the second and third columns, when the vector axis is that shown
  in the first column.
  <P>
  <PRE>
      Vector axis       |   Sum axis in 2D    |  Sum axes in 3D
      ------------------|---------------------|--------------------
           1            |         2           |      2 3                 
           2            |         1           |      1 3                 
           3            |         -           |      1 2                 
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>RVIDLINES V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='RVIDLINES' Line='RVIDLINES V2.11'>
  <DD>This task will now work in the units of the input spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>RVIDLINES V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='RVIDLINES' Line='RVIDLINES V2.10.3'>
  <DD>This is a new task in this version. 
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  center1d, fxcor, gtools, identify, keywpars, observatory,
  rvcorrect, rvreidlines
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'ADDTIONAL PARAMETERS' 'CURSOR KEYS' 'DESCRIPTION' 'DATABASE RECORDS' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
