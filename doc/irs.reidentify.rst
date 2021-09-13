.. _reidentify:

reidentify — Automatically identify features in spectra
=======================================================

**Package: irs**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  reidentify -- Reidentify features
  </UL>
  <! EndSection:   'NAME'>
  <H3>Summary</H3>
  <! BeginSection: 'SUMMARY'>
  <UL>
  Given a reference vector with identified features and (optionally) a
  coordinate function find the same features in other elements of the
  reference image and fit a new dispersion function or determine a
  zero point shift.  After all vectors of the reference image are
  reidentified use the reference vectors to reidentify corresponding
  vectors in other images.  This task is used for transferring dispersion
  solutions in arc calibration spectra and for mapping geometric and
  dispersion distortion in two and three dimensional images.
  </UL>
  <! EndSection:   'SUMMARY'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  reidentify reference images
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>reference</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>Image with previously identified features to be used as features reference for
  other images.  If there are multiple apertures, lines, or columns in the
  image a master reference is defined by the <I>section</I> parameter.
  The other apertures in multispec images or other lines, or columns
  (selected by <I>step</I>) are reidentified as needed.
  </DD>
  </DL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of images in which the features in the reference image are to be
  reidentified.  In two and three dimensional images the reidentifications are
  done by matching apertures, lines, columns, or bands with those in the reference
  image.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Examine and fit features interactively?  If the task is run interactively a
  query (which may be turned off during execution) will be given for each
  vector reidentified after printing the results of the automatic fit and the
  user may chose to enter the interactive <B>identify</B> task.
  </DD>
  </DL>
  <DL>
  <DT><B>section = "<TT>middle line</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = "middle line"'>
  <DD>If the reference image is not one dimensional or specified as a one dimensional
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
  is used with three dimensional data.  See the example section for
  <B>identify</B> for examples of this syntax.  Abbreviations are allowed
  though beware that <TT>'l'</TT> is not a sufficient abbreviation.
  </DD>
  </DL>
  <DL>
  <DT><B>newaps = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newaps' Line='newaps = yes'>
  <DD>Reidentify new apertures in the images which are not in the reference
  image?  If no, only apertures found in the reference image will be
  reidentified in the other images.  If yes, the master reference spectrum
  is used to reidentify features in the new aperture and then the
  new aperture solution will be added to the reference apertures.  All
  further identifications of the new aperture will then use this solution.
  </DD>
  </DL>
  <DL>
  <DT><B>override = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='override' Line='override = no'>
  <DD>Override previous solutions?  If there are previous solutions for a
  particular image vector being identified, because of a previous
  <B>identify</B> or <B>reidentify</B>, this parameter selects whether
  to simply skip the reidentification or do a reidentification and
  overwrite the solution in the database.
  </DD>
  </DL>
  <DL>
  <DT><B>refit = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refit' Line='refit = yes'>
  <DD>Refit the coordinate function?  If yes and there is more than one feature
  and a coordinate function was defined in the reference image database then a new
  coordinate function of the same type as in the reference is fit
  using the new pixel positions.  Otherwise only a zero point shift is
  determined for the revised coordinates without changing the
  form of the coordinate function.
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
  <DD>The step from the reference line, column, or band used for selecting and/or
  reidentifying additional lines, columns, or bands in a two or three
  dimensional reference image.  For three dimensional images there may be two
  numbers to allow independent steps along different axes.  If the step is
  zero then only the reference aperture, line, column, or band is used.  For
  multiaperture images if the step is zero then only the requested aperture
  is reidentified and if it is non-zero (the value does not matter) then all
  spectra are reidentified.  For long slit or Fabry-Perot images the step is
  used to sample the image and the step should be large enough to map any
  significant changes in the feature positions.
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
  the first number is used for both axes.  This parameter is not used for
  multispec type images.
  </DD>
  </DL>
  <DL>
  <DT><B>shift = "<TT>0</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shift' Line='shift = "0"'>
  <DD>Shift in user coordinates to be added to the reference features before
  centering.  If the image is three dimensional then two numbers may be
  specified for the two axes.  Generally no shift is used by setting the
  value to zero.  When stepping to other lines, columns, or bands in the
  reference image the shift is added to the primary reference spectrum if not
  tracing.  When tracing the shift is added to last spectrum when stepping to
  higher lines and subtracted when stepping to lower lines.  If a value
  if INDEF is specified then an automatic algorithm is applied to find
  a shift.
  </DD>
  </DL>
  <DL>
  <DT><B>search = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='search' Line='search = 0.'>
  <DD>If the <I>shift</I> parameter is specified as INDEF then an automatic
  search for a shift is made.  There are two algorithms.  If the search
  value is INDEF then a cross-correlation of line peaks is done.  Otherwise
  if a non-zero value is given then a pattern matching algorithm (see
  <I>autoidentify</I>) is used.  A positive value specifies the search radius in
  dispersion units and a negative value specifies a search radius as a
  fraction of the reference dispersion range.
  </DD>
  </DL>
  <DL>
  <DT><B>nlost = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlost' Line='nlost = 0'>
  <DD>When reidentifying features by tracing, if the number of features not found
  in the new image vector exceeds this number then the reidentification
  record is not written to the database and the trace is terminated.  A
  warning is printed in the log and in the verbose output.
  </DD>
  </DL>
  <P>
  The following parameters define the finding and recentering of features.
  See also <B>center1d</B>.
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
  <DT><B>threshold = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 0.'>
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
  <DT><B>coordlist = "<TT>linelists$idhenear.dat</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coordlist' Line='coordlist = "linelists$idhenear.dat"'>
  <DD>User coordinate list consisting of a list of line coordinates.
  Some standard line lists are available in the directory "<TT>linelists$</TT>".
  The standard line lists are described under the topic <I>linelists</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>match = -3.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='match' Line='match = -3.'>
  <DD>The maximum difference for a match between the feature coordinate function
  value and a coordinate in the coordinate list.  Positive values
  are in user coordinate units and negative values are in units of pixels.
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
  <DD>List of files in which to keep a processing log.  If a null file, "<TT></TT>",
  is given then no log is kept.
  </DD>
  </DL>
  <DL>
  <DT><B>plotfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = ""'>
  <DD>Optional file to contain metacode plots of the residuals.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print reidentification information on the standard output?
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
  <P>
  The following parameters are queried when the <TT>'b'</TT> key is used in the
  interactive review.
  <DL>
  <DT><B>crval, cdelt</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='crval' Line='crval, cdelt'>
  <DD>These parameters specify an approximate coordinate value and coordinate
  interval per pixel when the automatic line identification
  algorithm (<TT>'b'</TT> key) is used.  The coordinate value is for the
  pixel specified by the <I>crpix</I> parameter in the <B>aidpars</B>
  parameter set.  The default value of <I>crpix</I> is INDEF which then
  refers the coordinate value to the middle of the spectrum.  By default
  only the magnitude of the coordinate interval is used.  Either value
  may be given as INDEF.  In this case the search for a solution will
  be slower and more likely to fail.  The values may also be given as
  keywords in the image header whose values are to be used.
  </DD>
  </DL>
  <DL>
  <DT><B>aidpars = "<TT></TT>" (parameter set)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aidpars' Line='aidpars = "" (parameter set)'>
  <DD>This parameter points to a parameter set for the automatic line
  identification algorithm.  See <I>aidpars</I> for further information.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Features (spectral lines, cross-dispersion profiles, etc.) identified in a
  single reference vector (using the tasks <B>identify</B> or
  <B>autoidentify</B>) are reidentified in other reference vectors and the set
  of reference vectors are reidentified in other images with the same type of
  vectors.  A vector may be a single one dimensional (1D) vector in a two or
  three dimensional (2D or 3D) image, the sum of neighboring vectors to form
  a 1D vector of higher signal, or 1D spectra in multiaperture images.  The
  number of vectors summed in 2D and 3D images is specified by the parameter
  <I>nsum</I>.  This parameter does not apply to multiaperture images.
  <P>
  As the previous paragraph indicates, there are two stages in this task.
  The first stage is to identify the same features from a single reference
  vector to a set of related reference vectors.  This generally consists
  of other vectors in the same reference image such as other lines or
  columns in a long slit spectrum or the set of 1D aperture spectra in
  a multiaperture image.  In these cases the vectors are identified by
  a line, column, band, or aperture number.  The second stage is to
  reidentify the features from the reference vectors in the matching
  vectors of other images.  For example the same lines in the reference
  image and another image or the same apertures in several multiaperture
  images.  For multiaperture images the reference vector and target vector
  will have the same aperture number but may be found in different image
  lines.  The first stage may be skipped if all the reference vectors
  have been identified.
  <P>
  If the images are 2D or 3D or multiaperture format and a <I>step</I> greater
  than zero is specified then additional vectors (lines/columns/bands) in the
  reference image will be reidentified from the initial master reference
  vector (as defined by an image section or <I>section</I> parameter) provided
  they have not been reidentified previously or the <I>override</I> flag is
  set.  For multiple aperture spectral images, called multiaperture, a step
  size of zero means don't reidentify any other aperture and any other step
  size reidentifies all apertures.  For two and three dimensional images,
  such as long slit and Fabry-Perot spectra, the step(s) should be large
  enough to minimize execution time and storage requirements but small enough
  to follow shifts in the features (see the discussion below on tracing).
  <P>
  The reidentification of features in other reference image vectors
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
  added to the list of apertures to be reidentified in other images.
  This is useful when spectra with different aperture numbers are
  stored as one dimensional images.
  <P>
  The reidentification of features between a reference vector and
  a target vector is done as follows.  First a mean shift between
  the two vectors is determined.  After correcting for the shift
  the estimated pixel position of each reference feature in the
  target vector is used as the starting point for determining
  a feature center near this position.  The centering fails the
  feature is dropped and a check against the <I>nlost</I> is made.
  If it succeeds it is added to the list of features found in the
  target spectrum.  A zero point shift or new dispersion
  function may be determined.  New features may then be added from
  a coordinate list.  The details are given below.
  <P>
  There may be a large shift between the two vectors such that the same
  feature in the target vector is many pixels away from the pixel position in
  the reference spectrum.  A shift must then be determined.   The <I>shift</I>
  parameter may be used to specify a shift.  The shift is in user coordinates
  and is added to the reference user coordinates before trying to center
  on a feature.  For example if the reference spectrum has a feature at
  5015A but in the new spectrum the feature is at 5025A when the reference
  dispersion function is applied then the shift would be +10.  Thus
  a reference feature at 5015A would have the shift added to get 5025A,
  then the centering would find the feature some pixel value and that
  pixel value would be used with the true user coordinate of 5015A in the
  new dispersion solution.
  <P>
  When tracing a 2D/3D reference spectrum the shift is applied to the
  previous reidentified spectrum rather than the initial reference spectrum.
  The shift is added for increasing line or column values and subtracted for
  decreasing line or column values.  This allows "<TT>tracing</TT>" when there is a
  rotation or tilt of the 2D or 3D spectrum.  When not tracing the shift is
  always added to the reference spectrum features as described previously.
  <P>
  When reidentify other images with the reference spectrum the shift
  parameter is always just added to the reference dispersion solution
  matching the aperture, line, or column being reidentified.
  <P>
  If the <I>shift</I> parameter is given as INDEF then an automatic
  search algorithm is applied.  There are two algorithms that may be
  used.  If the <I>search</I> parameter is INDEF then a cross-correlation
  of the features list with the peaks found in the target spectrum is
  performed.  This algorithm can only find small shifts since otherwise
  many lines may be missing off either end of the spectrum relative to
  the reference spectrum.
  <P>
  If the search parameter is non-zero then the pattern matching algorithm
  described in <I>aidpars</I> is used.  The search parameter specified a
  search radius from the reference solution.  If the value is positive the
  search radius is a distance in dispersion units.  If the value is negative
  then the absolute value is used as a fraction of the dispersion range in
  the reference solution.  For example, a value of -0.1 applied to reference
  dispersion solution with a range of 1000A would search for a new solution
  within 100A of the reference dispersion solution.
  <P>
  The pattern matching algorithm has to stages.  First if there are
  more than 10 features in the reference the pattern matching tries
  to match the lines in the target spectrum to those features with
  a dispersion per pixel having the same sign and a value within 2%.
  If no solution is found then the <I>linelist</I> is used to match
  against the lines in the target spectrum, again with the dispersion
  per pixel having the same sign and a value within 5%.  The first
  stage works when the set of features is nearly the same while the
  second stage works when the shifts are large enough that many features
  in the reference and target spectra are different.
  <P>
  The centering algorithm is described under the topic <I>center1d</I> and
  also in <B>identify</B>.  If a feature positions shifts by more than the
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
  If a fitting function is defined for the features in the reference image,
  say a dispersion function in arc lamp spectra, then the function is refit
  at each reidentified line or column if the parameter <I>refit</I> is yes.
  If refitting is not selected then a zero point shift in the user
  coordinates is determined without changing the form of the fitting
  function.  The latter may be desirable for tracking detector shifts through
  a sequence of observation using low quality calibration spectra.  When
  refitting, the fitting parameters from the reference are used including
  iterative rejection parameters to eliminate misidentifications.
  <P>
  If the parameter <I>addfeatures</I> is set additional features may be added
  from a line list.  If there are reference features then the new features
  are added AFTER the initial reidentification and function fit.  If the
  reference consists only of a dispersion function, that is it has no
  features, then new features will be added followed by a function fit and
  then another pass of adding new features.  A maximum number of added
  features, a matching distance in user coordinates, and a minimum separation
  from other features are additional parameters.  This option is similar to
  that available in <B>identify</B> and is described more fully in the help
  for that task.
  <P>
  A statistics line is generated for each reidentified vector.  The line
  contains the name of the image being reidentified (which for two
  dimensional images includes the image section and for multiaperture
  spectra includes the aperture number), the number of features found
  relative to the number of features in the reference, the number of
  features used in the function fit relative to the number found,  the
  mean pixel, user coordinate, and fractional user coordinate shifts
  relative to the reference coordinates, and the RMS relative to the
  final coordinate system (whether refit or simply shifted) excluding any
  iteratively rejected features from the calculation.
  <P>
  If the task is run with the <I>interactive</I> flag the statistics line
  is printed to the standard output (the terminal) and a query is
  made whether to examine and/or refit the features.  A response
  of yes or YES will put the user in the interactive graphical mode
  of <B>identify</B>.  See the description of this task for more
  information.  The idea is that one can monitor the statistics information,
  particularly the RMS if refitting, and select only those which may be
  questionable to examine interactively.  A response of no or NO will
  continue on to the next reidentification.  The capitalized responses
  turn off the query and act as permanent response for all other
  reidentifications.
  <P>
  This statistics line, including headers, is written to any specified
  log files.  The log information includes the image being
  reidentified and the reference image, and the initial shift.
  <P>
  If an accessible file name is given for the plot file then a residual plot
  of the reidentified lines is recorded in this file.  The plot file can
  be viewed with <B>gkimosaic, stdgraph</B> or reading the file
  with "<TT>.read</TT>" when in cursor mode (for example with "<TT>=gcur</TT>").
  <P>
  The reidentification results for this task are recorded in a
  <I>database</I>.  Currently the database is a directory and entries
  in the database are text files with filenames formed by adding
  the prefix "<TT>id</TT>" to the image name without an image extension.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Arc lines and a dispersion solution were defined for the middle
  aperture in the multispec for arc spectrum a042.ms.  To reidentify the
  other apertures in the reference image and then another arc image:
  <P>
  <PRE>
    cl&gt; reiden a042.ms a045.ms inter+ step=1 ver+
    REIDENTIFY: NOAO/IRAF V2.9 valdes@puppis Fri 29-Jun-90
      Reference image = a042.ms.imh, New image = a042.ms, Refit = yes
       Image Data    Found     Fit Pix Shift  User Shift     RMS
    a042.ms - Ap 24  48/48   47/48   -2.38E-4    -3.75E-6  0.699
    Fit dispersion function interactively? (no|yes|NO|YES) (yes): y
    a042.ms - Ap 24  48/48   47/48   -2.38E-4    -3.75E-6  0.699
    a042.ms - Ap 23  48/48   47/48      0.216        1.32  0.754
    Fit dispersion function interactively? (no|yes|NO|YES) (yes): n
    a042.ms - Ap 22  48/48   47/48     0.0627       0.383  0.749
    Fit dispersion function interactively? (no|yes|NO|YES) (yes): n
    a042.ms - Ap 21  48/48   47/48      0.337        2.06  0.815
    &lt;etc&gt;
      Reference image = a042.ms.imh, New image = a045.ms, Refit = yes
       Image Data    Found     Fit Pix Shift  User Shift     RMS
    a045.ms - Ap 24  48/48   47/48   -2.38E-4    -3.75E-6  0.699
    Fit dispersion function interactively? (no|yes|NO|YES) (yes): y
    a045.ms - Ap 24  48/48   47/48   -2.38E-4    -3.75E-6  0.699
    a045.ms - Ap 23  48/48   47/48      0.216        1.32  0.754
    Fit dispersion function interactively? (no|yes|NO|YES) (yes): N
    a045.ms - Ap 22  48/48   47/48     0.0627       0.383  0.749
    a042.ms - Ap 21  48/48   47/48      0.337        2.06  0.815
    a042.ms - Ap 20  48/48   47/48     -0.293       -1.79  0.726
    a042.ms - Ap 19  48/48   48/48      0.472        2.88  0.912
  </PRE>
  <P>
  This example is verbose and includes interactive review of reidentifications.
  The statistics lines have been shortened.
  <P>
  2.  To trace a stellar profile and arc lines in long slit images for the
  purpose of making a distortion correction:
  <P>
  <PRE>
    cl&gt; reiden rog022[135,*] "" trace+
    cl&gt; reiden rog023 "" sec="mid line" trace+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>REIDENTIFY V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='REIDENTIFY' Line='REIDENTIFY V2.11'>
  <DD>The <I>search</I> parameter and new searching algorithm has been added.
  <P>
  The task will now work with only a warning if the reference image is absent;
  i.e. it is possible to reidentify given only the database.
  <P>
  The <I>addfeatures</I> function will now add features before a fit if there
  are no reference database features.  Previously features could only be
  added after an initial fit using the reference features and, so, required
  the reference database to contain features for reidentification.  This
  new feature is useful if one wants to uses a dispersion function from one
  type of calibration but wants to add features for a different kind of
  calibration.
  </DD>
  </DL>
  <DL>
  <DT><B>REIDENTIFY V2.10.3</B></DT>
  <! Sec='REVISIONS' Level=0 Label='REIDENTIFY' Line='REIDENTIFY V2.10.3'>
  <DD>The section, nsum, step, and shift parameter syntax was extended to apply to 3D
  images.  The previous values and defaults may still be used.
  <P>
  For multiaperture data a step of zero selects only the reference aperture
  to be reidentified and any other step selects reidentifying all apertures.
  </DD>
  </DL>
  <DL>
  <DT><B>REIDENTIFY V2.10</B></DT>
  <! Sec='REVISIONS' Level=0 Label='REIDENTIFY' Line='REIDENTIFY V2.10'>
  <DD>This task is a new version with many new features.  The new features
  include an interactive options for reviewing identifications, iterative
  rejection of features during fitting, automatic addition of new features
  from a line list, and the choice of tracing or using a single master
  reference when reidentifying features in other vectors of a reference
  spectrum.  Reidentifications from a reference image to another image is
  done by matching apertures rather than tracing.  New apertures not present
  in the reference image may be added.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  autoidentify, identify, aidpars, center1d, linelists, fitcoords
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SUMMARY' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
