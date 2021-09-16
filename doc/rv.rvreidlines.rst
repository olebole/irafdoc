.. _rvreidlines:

rvreidlines — Reidentify spectral lines and measure radial velocities
=====================================================================

**Package: rv**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  rvreidlines -- Reidentify spectral lines and measure velocities
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  rvreidlines reference images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>reference</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>Spectrum with previously identified features to be used as reference for
  other spectra.  If there are multiple apertures, lines, or columns in the
  image a master reference is defined by the <I>section</I> parameter.
  The other apertures, lines, or columns selected by <I>step</I> are
  reidentified if needed.
  </DD>
  </DL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of dispersion corrected spectral images in which the features in the
  reference image are to be reidentified.  In two and three dimensional
  images the reidentifications are done by matching apertures, lines,
  columns, or bands with those in the reference image.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Examine and fit features and velocities interactively?  If the task is run
  interactively a query (which may be turned off during execution) will be
  given for each vector reidentified after printing the results of the
  automatic determination and the user may chose to enter the interactive
  <B>rvidlines</B> task.
  </DD>
  </DL>
  <DL>
  <DT><B>section = "<TT>middle line</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = "middle line"'>
  <DD>If the reference image is not one dimensional or given as a one dimensional
  image section then this parameter selects the master reference image
  vector.  The master reference is used when reidentifying other vectors in
  the reference image or when other images contain apertures not present in
  the reference image.  This parameter also defines the direction
  (columns, lines, or z) of the image vectors to be reidentified.
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
  which is an integer number.  The field in [] is a second designator which
  is used with 3D data.  See the example section for <B>rvidlines</B> for
  examples of this syntax.  Abbreviations are allowed though beware that <TT>'l'</TT>
  is not a sufficient abbreviation.
  </DD>
  </DL>
  <DL>
  <DT><B>newaps = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newaps' Line='newaps = yes'>
  <DD>Reidentify new apertures in the images which are not in the reference
  image?  If no, only apertures found in the reference image will be
  reidentified in the other images.  If yes, the master reference spectrum
  is used to reidentify features in the new aperture and then the
  new aperture features will be added to the reference apertures.  All
  further identifications of the new aperture will then use this result.
  </DD>
  </DL>
  <DL>
  <DT><B>override = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='override' Line='override = no'>
  <DD>Override previous solutions?  If there are previous measurements for a
  particular image vector being identified, because of a previous
  <B>rvidlines</B> or <B>rvreidlines</B>, this parameter selects whether
  to simply skip the reidentification or do a reidentification and
  velocity measurement and overwrite the results in the logfile and database.
  </DD>
  </DL>
  <P>
  The following parameters are used for selecting and reidentifying additional
  lines, columns, or apertures in two dimensional formats.
  <DL>
  <DT><B>trace = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='trace' Line='trace = no'>
  <DD>There are two methods for defining additional reference lines, columns, or
  bands in two and three dimensional format images as selected by the
  <I>step</I> parameter.  When <I>trace</I> is no the master reference line or
  column is used for each new reference vector.  When this parameter is yes
  then as the reidentifications step across the image the last reidentified
  features are used as the reference.  This "<TT>tracing</TT>" is useful if there is a
  coherent shift in the features such as with long slit spectra.  However,
  any features lost during the tracing will be lost for all subsequent lines
  or columns while not using tracing always starts with the initial set of
  reference features.
  </DD>
  </DL>
  <DL>
  <DT><B>step = "<TT>10</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='step' Line='step = "10"'>
  <DD>The step from the reference aperture, line, column, or band used for
  selecting and/or reidentifying additional lines, columns, or bands in a two
  or three dimensional reference image.  For three dimensional images there
  may be two numbers to allow independent steps along different axes.  For
  multiaperture images the step is typically 1 while for long slit or
  Fabry-Perot images the step is large enough to map any significant changes
  in the feature positions.  If the step is zero then only the reference
  line, column, or band is used.
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
  <DT><B>shift = "<TT>0</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shift' Line='shift = "0"'>
  <DD>Shift in user coordinates to be added to the reference features before
  centering when stepping to other lines, columns, or bands in the reference
  image.  Generally no shift is used by setting the value to zero.
  The shift is used as a slope with positive values increasing towards
  larger line or column numbers.  This parameter is not used for
  reidentifications from the reference image to other images.
  If the image is three dimensional then two numbers may be specified
  for the two axes.
  </DD>
  </DL>
  <DL>
  <DT><B>nlost = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlost' Line='nlost = 0'>
  <DD>When reidentifying features by tracing, if the number of features not found
  in the new image vector exceeds this number then the reidentification
  record is not written to the logfile and database and the trace is terminated.  A warning is printed in the log and in the verbose output.
  </DD>
  </DL>
  <P>
  The following parameters define the finding and recentering of features.
  See also <B>center1d</B> and <B>rvidlines</B>.
  <DL>
  <DT><B>cradius = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cradius' Line='cradius = 5.'>
  <DD>Centering radius in pixels.  If a reidentified feature falls further
  than this distance from the previous line or column when tracing or
  from the reference feature position when reidentifying a new image
  then the feature is not reidentified.
  </DD>
  </DL>
  <DL>
  <DT><B>threshold = 10.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 10.'>
  <DD>In order for a feature center to be determined, the range of pixel
  intensities around the feature must exceed this threshold.  This parameter
  is used to exclude noise peaks and terminate tracing when the signal
  disappears.  However, failure to properly set this parameter, particularly
  when the data values are very small due to normalization or flux
  calibration, is a common error leading to failure of the task.
  </DD>
  </DL>
  <P>
  The following parameters select and control the automatic addition of
  new features during reidentification.
  <DL>
  <DT><B>addfeatures = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='addfeatures' Line='addfeatures = no'>
  <DD>Add new features from a line list during each reidentification?  If
  yes then the following parameters are used.  This function can be used
  to compensate for lost features from the reference solution, particularly
  when tracing.  Care should be exercised that misidentified features
  are not introduced.
  </DD>
  </DL>
  <DL>
  <DT><B>coordlist = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coordlist' Line='coordlist = ""'>
  <DD>User coordinate list consisting of an ordered list of rest spectral line
  coordinates.
  </DD>
  </DL>
  <DL>
  <DT><B>match = 10.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='match' Line='match = 10.'>
  <DD>The maximum difference for a match between the feature coordinate function
  value and a coordinate in the coordinate list (after correction by the
  velocity).
  </DD>
  </DL>
  <DL>
  <DT><B>maxfeatures = 50</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxfeatures' Line='maxfeatures = 50'>
  <DD>Maximum number of the strongest features to be selected automatically from
  the coordinate list.
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
  The following parameters determine the input and output of the task.
  <DL>
  <DT><B>database = "<TT>database</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "database"'>
  <DD>Database containing the feature data for the reference image and in which
  the features for the reidentified images are recorded.
  </DD>
  </DL>
  <DL>
  <DT><B>logfiles = "<TT>logfile</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfiles' Line='logfiles = "logfile"'>
  <DD>List of file in which to record the velocity results and to keep a
  processing log.  If a null file, "<TT></TT>", is given then no log is kept.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print reidentification and velocity information on the standard output?
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
  ADDTIONAL PARAMETERS
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
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Rvreidlines</B> takes spectral lines previously identified in a reference
  image and recorded in a database and identifies them in other spectra and
  determines a radial velocity.  If the images are
  two or three dimensional or multiaperture format and a <I>step</I> greater
  than zero is specified then additional vectors
  (lines/columns/bands/apertures) in the reference image will be reidentified
  from the initial master reference vector (as defined by an image section or
  <I>section</I> parameter) provided they have not been reidentified
  previously or the <I>override</I> flag is set.  For multiple aperture
  spectra images, called multiaperture, the step size is typically 1; i.e.
  reidentify features in all spectra.  For two and three dimensional images,
  such as long slit and Fabry-Perot spectra, the step(s) should be large enough
  to minimize execution time and storage requirements but small enough to
  follow shifts in the features (see the discussion below on tracing).  The
  set of reference identifications is applied to other images in the same
  lines, columns, bands, or apertures.  In multiaperture images the same
  apertures are matched in the reference image regardless of actual line
  order; i.e.  the apertures need not be in the same order or even have all
  apertures present.
  <P>
  The reidentification of other features in other reference image vectors
  may be done in two ways selected by the parameter <I>trace</I>.  If not
  tracing, the initial reference vector is applied to the other selected
  vectors.  If tracing, the reidentifications are made with respect to the
  last set of identifications as successive steps away from the reference
  vector are made.  The tracing method is appropriate for two and three
  dimensional spatial images, such as long slit and Fabry-Perot spectra, in
  which the positions of features traced vary smoothly.  This allows
  following large displacements from the initial reference by using suitably
  small steps.  It has the disadvantage that features lost during the
  reidentifications will not propagate (unless the <I>addfeatures</I> option
  is used).  By not tracing, the original set of features is used for every
  other vector in the reference image.
  <P>
  When reidentifying other vectors in the reference image the parameter
  <B>shift</B> may be used to add a shift(s) to the features positions
  before recentering.  The shift is added to lines, columns, or bands, greater
  than the current line, column, or band and subtracted if less.  If tracing
  the shifts are the same from step to step while if not tracing the
  shifts are added to the shifts from the previous step.  Thus, in both
  cases an approximation of a slope is used.  This allows large
  slopes in the features to be followed even when not tracing but the 
  shift value must be predetermined.
  <P>
  When tracing, the parameter <I>nlost</I> is used to terminate the
  tracing whenever this number of features has been lost.  This parameter,
  in conjunction with the other centering parameters which define
  when a feature is not found, may be useful for tracing features
  which disappear before reaching the limits of the image.
  <P>
  When reidentifying features in other images, the reference
  features are those from the same aperture, line, column, or band of the
  reference image.  However, if the <I>newaps</I> parameter is set
  apertures in multiaperture spectra which are not in the reference
  image may be reidentified against the master reference aperture and
  added to the list of aperture to be reidentified in other images.
  This is useful when specta with different aperture numbers are
  stored as one dimensional images.
  <P>
  There are two centering algorithms; a flux bisecting algorithm called
  <B>center1d</B> and a gaussian fitting algorithm.  These algorithms
  are described in the help for <B>rvidlines</B>.  The algorithm used
  and whether the feature is emission or absorption is the same one used
  in the reference image.  The only caveat is that multiple gaussian
  fitting provided by the interactive <TT>'b'</TT> key in <B>rvidlines</B> is
  not done by this task and those lines will be fit by gaussians
  independently.
  <P>
  When recentering, if a feature position shifts by more than the
  amount set by the parameter <I>cradius</I> from the starting position
  (possibly after adding a shift) or the feature strength (peak to valley) is
  less than the detection <I>threshold</I> then the new feature is discarded.
  The <I>cradius</I> parameter should be set large enough to find the correct
  peak in the presence of any shifts but small enough to minimize incorrect
  identifications.  The <I>threshold</I> parameter is used to eliminate
  identifications with noise.  Failure to set this parameter properly for the
  data (say if data values are very small due to a calibration or
  normalization operation) is the most common source of problems in using
  this task.
  <P>
  In two and three dimensional images, though not multiaperture images, the
  number of lines, columns, or bands given by the parameter <I>nsum</I> are summed
  to form the one dimensional image vector in which the features are
  identified.  This increases the accuracy for reidentifying weak
  features.
  <P>
  If the parameter <I>addfeatures</I> is set additional features may be added
  after the initial reidentification and velocity determination using a line
  list of rest wavelengths.  A maximum number of added features, a matching
  distance in user coordinates, and a minimum separation from other features
  are additional parameters.  This option is similar to that available in
  <B>rvidlines</B> and is described more fully in the help for that task.
  <P>
  A statistics line is generated for each reidentified vector.  The line
  contains the name of the image being reidentified (which for two
  dimensional images includes the image section and for multiaperture
  spectra includes the aperture number), the number of features found
  relative to the number of features in the reference, the number of
  features used in the velocity determination (currently there is
  no rejection of lines) relative to the number found,  the
  mean pixel and user coordinate shfits relative to the reference
  coordinates, and the measured velocity and RMS in the velocity.
  The velocity is the heliocentric velocity if the necessary observation
  information in the image and observatory database are found.
  <P>
  If the task is run with the <I>interactive</I> flag the statistics line
  is printed to the standard output (the terminal) and a query is
  made whether to fit the lines and measure the velocity interactively.
  A response
  of yes or YES will put the user in the interactive graphical mode
  of <B>rvidlines</B>.  See the description of this task for more
  information.  The idea is that one can monitor the statistics information,
  particularly the velocity RMS, and select only those which may be
  questionable to examine interactively.  A response of no or NO will
  continue on to the next spectrum.  The capitalized responses
  turn off the query and act as permanent response for all other
  reidentifications.
  <P>
  This statistics line, including headers, is written to any specified
  log files.  The log information includes the image being
  reidentified and the reference image.
  In addition the set of lines, the observatory information used,
  and the computed observed and heliocentric velocities and redshifts
  are recorded.  This is the same information as is produced
  by <B>rvidlines</B>.
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
  read and written by <B>rvreidlines</B> have "<TT>identify</TT>" as the first word of the
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
  1.  To generate a rotation curve for a long slit spectrum of a
  galaxy first use <B>rvidlines</B> to mark some lines at the center of the
  galaxy.  If the velocities are to be absolute then you give the rest
  wavelengths and do a fit.  However to get velocities relative to the center
  use the measured wavelengths by simply accepting the prompted measured
  wavelengths.  Then run <B>rvreidlines</B>.  The <I>nsum</I> and <I>step</I>
  parameters allow controlling the summing size and spacing.
  <P>
  <PRE>
      rv&gt; rvid lsgal sec="mid col" nsum=5
  	    Mark lines and then quit.
      Write velocity data to the logfile (yes)?
      Write feature data to the database (yes)?
      rv&gt; rvreid lsgal "" sec="mid col" nsum=5 step=5 trace+ v+
  <P>
      RVREIDLINES: NOAO/IRAF V2.10.3 valdes Sat 14:47:55 21-Aug-93
        Reference image = lsgal, New image = lsgal
       Image Data  Found    Fit  Pix Shift  User Shift Velocity    RMS
      lsgal[45,*]    7/7    7/7    -0.0181     -0.0212    -1.37   11.3
      lsgal[40,*]    7/7    7/7     0.0147      0.0193     1.34   8.73
      lsgal[35,*]    7/7    7/7     0.0931       0.116     8.01   9.16
      lsgal[30,*]    7/7    7/7    -0.0224     -0.0265    -1.78   27.6
      lsgal[25,*]    7/7    7/7     0.0558        0.07     4.83   33.7
      lsgal[20,*]    7/7    7/7    -0.0317     -0.0379    -3.08   33.6
      lsgal[15,*]    5/7    5/5      0.015      0.0201    0.799   43.7
      lsgal[10,*]    7/7    7/7      0.395       0.489     33.7   54.9
      lsgal[5,*]     4/7    4/4      -1.22       -1.51    -106.   84.3
      lsgal[55,*]    7/7    7/7      0.014      0.0184     1.41   10.5
      lsgal[60,*]    7/7    7/7    -0.0897      -0.109    -7.59   7.21
      lsgal[65,*]    7/7    7/7    -0.0109     -0.0122   -0.957   10.9
      lsgal[70,*]    7/7    7/7     -0.074     -0.0902    -6.55   14.6
      lsgal[75,*]    7/7    7/7   -0.00203    -0.00136    0.227   54.3
      lsgal[80,*]    6/7    6/6       0.08      0.0997     6.66   96.7
      lsgal[85,*]    6/7    6/6      0.289       0.357     27.2   104.
      lsgal[90,*]    6/7    6/6      0.459       0.568     40.5   33.2
      lsgal[95,*]    6/7    6/6      0.926        1.14     78.5   65.5
      lsgal[100,*    5/7    5/5      0.696        0.86     59.1   44.2
      rv&gt; match Vobs logfile | fields "" 2,6,11 | \<BR>
      &gt;&gt;&gt; graph point- mark=vebar szmark=-1
  </PRE>
  <P>
  The last command extracts the Vobs results from the logfile using
  <B>match</B>, the column number, velocity, and mean error are extract
  using <B>fields</B>, and graphs the points with error bars.  One
  drawback to this method is that the nubmer of columns summed is
  constant and so the signal-to-noise decreases with the galaxy light.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>RVREIDLINES V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='RVREIDLINES' Line='RVREIDLINES V2.11'>
  <DD>This task will now work in the units of the input spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>RVREIDLINES V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='RVREIDLINES' Line='RVREIDLINES V2.10.3'>
  <DD>This task in new in the version.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  center1d, fxcor, keywpars, observatory, rvcorrect, rvidlines
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'DATABASE RECORDS' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
