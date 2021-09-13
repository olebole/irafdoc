.. _linmatch:

linmatch — Match the linear intensity scales of 1-D or 2-D images
=================================================================

**Package: immatch**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  linmatch -- linearly match the intensity scales of 1 and 2D images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  linmatch input reference regions lintransform
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input images to be matched.
  </DD>
  </DL>
  <DL>
  <DT><B>reference</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>The list of reference images to which the input images are to be matched
  if <I>scaling</I>  is one of the "<TT>mean</TT>", "<TT>median</TT>", "<TT>mode</TT>", or "<TT>fit</TT>"
  algorithms, or the list of reference photometry files if <I>scaling</I>
  specifies the "<TT>photometry</TT>" algorithm. The number of reference images or
  reference photometry files must be one or equal to the number of input
  images.
  </DD>
  </DL>
  <DL>
  <DT><B>regions</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='regions' Line='regions'>
  <DD>The list of image regions used to compute the intensity 
  matching function if <I>scaling</I> is one of the "<TT>mean</TT>", "<TT>median</TT>", "<TT>mode</TT>",
  or "<TT>fit</TT>" algorithms, or a list of the input photometry files if
  <I>scaling</I> specifies the "<TT>photometry</TT>" algorithm. In the former
  case <I>regions</I> may be: 1) a string of the form "<TT>grid nx ny</TT>" defining
  a grid of nx by ny equally spaced and sized image regions spanning the
  entire image, 2) a list of object coordinates separated by commas e.g.
  "<TT>303 401, 131 202</TT>", 3) a list of image sections separated by whitespace
  e.g "<TT>[101:200,101:200] [301:400,301:400]</TT>",
  4) the name of a text file containing a list of object coordinates separated
  by newlines, and 5) the name of a text file containing a list of image
  sections separated by whitespace and/or newlines.
  </DD>
  </DL>
  <DL>
  <DT><B>lintransform</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lintransform' Line='lintransform'>
  <DD>The name of the text file where the computed scaling factors are written.
  If <I>databasefmt</I> is "<TT>yes</TT>", a single record containing the computed
  bscale and bzero factors for each image region or object, and the
  average bscale and bzero, is written to the text database
  file for each input image. If <I>databasefmt</I> = "<TT>no</TT>", a single line
  containing the input image name, bscale factor, bzero factor, error
  in bscale, and error in bzero is written to a simple text file for
  each image.
  </DD>
  </DL>
  <DL>
  <DT><B>output = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = ""'>
  <DD>The list of output matched images. If <I>output</I> is the NULL string
  then bscale  and bzero are computed for each input image and written to
  <I>lintransform</I>, but no output images are written. If <I>output</I>
  is not NULL then the number of output images must equal the number of
  input images.
  </DD>
  </DL>
  <DL>
  <DT><B>databasefmt = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='databasefmt' Line='databasefmt = yes'>
  <DD>If <I>databasefmt</I> is "<TT>yes</TT>" the computed bscale and bzero factors
  are written to a text database file, otherwise they are written to a
  simple text file.
  </DD>
  </DL>
  <DL>
  <DT><B>records = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records = ""'>
  <DD>The list of records to be written to or read from <I>lintransform</I> one
  input image. If <I>records</I> is NULL then the output or input record names
  are assumed to be the names of the input images. If <I>records</I> is not NULL
  then the record names in <I>records</I> are used to write / read the
  database records. This parameter is useful for users
  who, wish to compute the bscale and bzero factors using images that have
  been processed
  in some manner (e.g. smoothed), but apply the computed bscale and bzero
  factors to the original unprocessed images. If more than one record
  with the same name exists in <I>lintransform</I> then the most recently written
  record takes precedence. The records parameter is ignored if
  <I>databasefmt</I> is "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>append = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = yes'>
  <DD>Append new records to an existing <I>lintransform</I> file or start a new 
  file for each execution of LINMATCH? The append parameter is
  ignored if <I>databasefmt</I> is "<TT>no</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>shifts = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shifts' Line='shifts = ""'>
  <DD>An optional list of shifts files containing the x and y shifts to be applied
  to the reference regions to determine their positions in
  the input images. The number of shifts files must equal the number of
  reference images. The shifts are listed in the shifts file, 1 shift per line,
  with the x and y shifts in
  columns 1 and 2 respectively. If there are fewer x and y shifts defined
  in the shifts file than there are input images, the extra input
  images will be assigned x and y shifts of <I>xshift</I> and <I>yshift</I>
  respectively. The shifts parameter is ignored if the <I>scaling</I>
  parameter is set to "<TT>photometry</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>xshift = 0.0 yshift = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xshift' Line='xshift = 0.0 yshift = 0.0'>
  <DD>The default x and y shifts to be applied to the reference image regions
  or objects to compute their positions in the input image.
  Values in <I>shifts</I> take precedence over the values of <I>xshift</I> and
  <I>yshift</I>. xshift and yshift are ignored if the <I>scaling</I> parameter
  is set to "<TT>photometry</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>dnx = 31 dny = 31</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dnx' Line='dnx = 31 dny = 31'>
  <DD>The default size of a single image region used to compute the bscale
  and bzero factors if <I>scaling</I> is one of the "<TT>mean</TT>", "<TT>median</TT>", "<TT>mode</TT>",
  or "<TT>fit</TT>" algorithms and <I>regions</I> is a coordinate list rather than
  a sections list.  dnx and dny are ignored if the <I>scaling</I> parameter
  is set to "<TT>photometry</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>maxnregions = 100</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxnregions' Line='maxnregions = 100'>
  <DD>The maximum number of image regions or objects with measured photometry
  that can be used to compute the bscale and bzero factors.
  </DD>
  </DL>
  <DL>
  <DT><B>scaling = "<TT>mean mean</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scaling' Line='scaling = "mean mean"'>
  <DD>The algorithms used to compute the bscale and bzero factors respectively.
  The options are:
  <DL>
  <DT><B>mean median mode</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='mean' Line='mean median mode'>
  <DD>Bscale or bzero are computed using the "<TT>mean</TT>", "<TT>median</TT>", or "<TT>mode</TT>" statistic
  for each input and reference region individually. If one of the bscale or
  bzero fitting
  algorithms is set to "<TT>mean</TT>", "<TT>median</TT>", or "<TT>mode</TT>", the remaining factor
  must be set to "<TT>mean</TT>", "<TT>median</TT>" or "<TT>mode</TT>" or  a numerical constant,
  e.g. "<TT>mean mean</TT>", "<TT>mean -100.0</TT>" or "<TT>2.63 mode</TT>".
  If both algorithms are set to "<TT>mean</TT>", "<TT>median</TT>", or "<TT>mode</TT>" bscale will be
  computed using the specified statistic and bzero will be set to 0.0
  If more than one input region is defined then a weighted least squares
  fit of the reference statistics to the input image statistics  
  is performed and used to compute the final bscale and bzero factors.
  </DD>
  </DL>
  <DL>
  <DT><B>fit    </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='fit' Line='fit    '>
  <DD>Bscale and bzero are computed for each input image region individually
  by performing a least squares fit of the reference image pixels to
  the input image pixels. If more than one input image region is defined
  the final bscale and bzero factors are computed by averaging,
  weighted by their signal-to-noise ratios, the individual bscale and bzero
  values.  If one of the bscale or bzero fitting
  algorithms is set to "<TT>fit</TT>", the remaining factor must either also
  be computed with the "<TT>fit</TT>" algorithm  or set to a numerical constant,
  e.g. "<TT>fit fit</TT>", "<TT>fit -100.0</TT>", or "<TT>2.63 fit</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>photometry</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='photometry' Line='photometry'>
  <DD>Bscale and/or bzero are computed for each input object individually
  using photometry computed for a set of objects common to the reference
  and input images.  If more than one input object is defined
  the final bscale and bzero factors are computed by averaging,
  weighted by their signal-to-noise ratios, the individual bscale and bzero
  values.  If one of the bscale or bzero fitting
  algorithms is set to "<TT>photometry</TT>", the remaining factor must either also
  be computed with the "<TT>photometry</TT>" algorithm or set to a numerical
  constant, e.g. "<TT>photometry photometry</TT>", "<TT>photometry -100.0</TT>", or
  "<TT>2.63 photometry</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>number</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='number' Line='number'>
  <DD>Bscale and/or bzero are set to user defined numerical constants,
  e.g. "<TT>2.62 -55.0</TT>" or  "<TT>2.62 median</TT>". If both bscale and bzero are numerical
  constants, LINMATCH must be run in non-interactive mode. If only one of bscale
  or bzero is a numerical constant, any of the "<TT>mean</TT>", "<TT>median</TT>", "<TT>mode</TT>", "<TT>fit</TT>",
  or "<TT>photometry</TT>" algorithms may be used to compute the remaining factor.
  </DD>
  </DL>
  <DL>
  <DT><B>file</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='file' Line='file'>
  <DD>Bscale and bzero are not computed but instead read from record <I>record</I> in
  the text database file <I>lintransform</I> if <I>databasefmt</I> is "<TT>yes</TT>",
  or the next line of a simple text file if <I>databasefmt</I> is "<TT>no</TT>".
  </DD>
  </DL>
  <P>
  Further description of the matching algorithms can be found in the ALGORITHMS
  section.
  </DD>
  </DL>
  <DL>
  <DT><B>datamin = INDEF datamax = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datamin' Line='datamin = INDEF datamax = INDEF'>
  <DD>The minimum and maximum good data values. Datamin and datamax are used by
  the "<TT>mean</TT>", "<TT>median</TT>", and "<TT>mode</TT>" scaling algorithms to reject entire
  image regions from the final fit, and by the "<TT>fit</TT>" algorithm to reject
  individual bad pixels from the least squares fits for the individual
  regions.
  </DD>
  </DL>
  <DL>
  <DT><B>maxiter = 10</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxiter' Line='maxiter = 10'>
  <DD>The maximum number of iterations performed by the least squares fitting
  algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B>nreject = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nreject' Line='nreject = 0'>
  <DD>The maximum number of rejection cycles used to detect and reject bad pixels
  from the fit if the scaling algorithm is "<TT>fit</TT>" or bad regions / objects
  from the fit if the scaling algorithm is "<TT>mean</TT>", "<TT>median</TT>", "<TT>mode</TT>", "<TT>fit</TT>",
  or "<TT>photometry</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>loreject = INDEF hireject = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='loreject' Line='loreject = INDEF hireject = INDEF'>
  <DD>The high- and low-side bad data rejection limits used to detect and reject
  deviant pixels from the fit if the scaling algorithm is "<TT>fit</TT>" or bad
  regions / objects from the fit if the scaling algorithm is "<TT>mean</TT>", "<TT>median</TT>",
  "<TT>mode</TT>", "<TT>fit</TT>", or "<TT>photometry</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>gain = "<TT>1.0 1.0</TT>" readnoise = "<TT>0.0 0.0</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain = "1.0 1.0" readnoise = "0.0 0.0"'>
  <DD>The reference and input image gain and readout noise in e-/ADU and
  e- respectively. Gain and readout may be numerical constants or the
  image header keyword containing the actual gain and/or readout noise
  value. Gain and readnoise are used by the "<TT>mean</TT>", "<TT>median</TT>", "<TT>mode</TT>",
  and "<TT>fit</TT>" algorithms to estimate the expected errors in the computed
  "<TT>mean</TT>", "<TT>median</TT>", or "<TT>mode</TT>" statistics,  and by the "<TT>fit</TT>" algorithm
  to compute the per pixel errors values.
  </DD>
  </DL>
  <DL>
  <DT><B>interactive = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no'>
  <DD>Compute the bscale and bzero scaling factors for each image interactively
  using graphics cursor and optionally image cursor input.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about the progress of the task during task execution in
  non-interactive mode.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>The default graphics device.
  </DD>
  </DL>
  <DL>
  <DT><B>display = "<TT>stdimage</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='display' Line='display = "stdimage"'>
  <DD>The default image display device.
  </DD>
  </DL>
  <DL>
  <DT><B>gcommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""'>
  <DD>The default graphics cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>icommands = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""'>
  <DD>The default image cursor.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  LINMATCH computes the bscale and bzero factors required to match
  the intensity scales of a list of input
  images <I>input</I> to the intensity scales of a list of reference
  images <I>reference</I> using the following definition of
  bscale and bzero and a variety of techniques.
  <P>
  <PRE>
  	reference = bscale * input + bzero
  </PRE>
  <P>
  The computed bscale and bzero factors are stored
  in the text file <I>lintransform</I>, in the record <I>records</I> if
  <I>databasefmt</I> is "<TT>yes</TT>", or a single line of a simple text file
  if <I>databasefmt</I> is "<TT>no</TT>". One record is written to the output file
  file for each input image. If a non NULL list of output images
  <I>output</I> is supplied, a scaled output image is written for
  each input image. LINMATCH is intended to solve 1D and 2D image intensity
  matching problems where the input and reference images: 1) have the same
  pixel scale and orientation, 2) differ in intensity by at most a scale
  factor and a zero point, and 3) contain one or more regions or objects in
  common that can be used to compute the scaling factors. Some of the scaling
  algorithms also require that the images registered and have identical
  point spread functions. LINMATCH cannot be used to compute or apply non-linear
  intensity matching functions.
  <P>
  If <I>scaling</I> = "<TT>mean</TT>", "<TT>median</TT>", "<TT>mode</TT>", or "<TT>fit</TT>" bscale and bzero
  are computed directly from the input and reference image data using the
  image sections specified in the <I>regions</I> and one of the above fitting
  techniques as described in the ALGORITHMS section. All four algorithms
  require accurate knowledge of the measurement errors which in turn
  require accurate knowledge of the input and reference image gain and
  readout noise values. Gain and readout noise values can be entered by
  setting the <I>gain</I> and <I>readnouse</I> parameters to the appropriate
  numerical values or image header keyword.
  <P>
  <I>Regions</I> is interpreted as either: 1) a string of
  the form "<TT>grid nx ny</TT>" specifying a list of nx by ny image sections
  spanning the entire image, 2) a string defining the coordinates of a list
  of objects separated by commas e.g.
  "<TT>103.3 189.2, 204.4 389.7</TT>", 3) a string containing a list of image
  sections separated by whitespace, e.g "<TT>[100:203,200:300] [400:500,400:500]</TT>"
  4) the name of a text file containing the coordinates of one or
  more objects, one object per line, with the x and y coordinates
  in columns 1 and 2 respectively, 5) the name of a text
  file containing a list of image sections separated by whitespace and/or
  newlines.  The image sections specifications, or alternatively
  the object coordinates and the parameters <I>dnx</I> and <I>dny</I>,
  determine the size of the input and reference image data regions to be
  extracted and used to compute the bscale and bzero factors.
  These image regions should be selected with care. Ideal regions
  span a range of intensity values and contain both object and background
  data. 
  <P>
  If <I>scaling</I> = "<TT>photometry</TT>", the bscale and bzero factors
  are computed directly from data in the input and reference image photometry
  files using the technique described in the ALGORITHMS section.
  In this case <I>regions</I> is a list of the input image photometry
  files and <I>reference</I> are the corresponding reference image
  photometry files written by a separate photometry task.
  These photometry files are simple text files with the object
  sky values, errors in the sky values, magnitudes, and errors in the
  magnitudes in columns 1, 2, 3, and 4 respectively.
  <P>
  An image region is rejected from the fit if it contains data outside the
  limits specified by the <I>datamin</I> and <I>datamax</I> parameters
  and <I>scaling</I> =
  "<TT>mean</TT>", "<TT>median</TT>", or "<TT>mode</TT>". A pixel is rejected from the fit for an
  individual region if the pixel value is outside the limits specified
  by datamin and datamax, and the scaling algorithm is "<TT>fit</TT>". The datamin
  and datamax parameters are not used by the "<TT>photometry</TT>" scaling algorithm .
  <P>
  Deviant pixels can be rejected from the fits to individual image regions
  if <I>scaling</I> = "<TT>fit</TT>", and <I>nreject</I>, <I>loreject</I>, and
  <I>hireject</I> are set appropriately. Nreject, loreject and reject
  are also be used by all the scaling algorithms  to reject image regions
  which contribute deviant bscale and bzero values.
  <P>
  The computed bscale and bzero value for each region and the final bscale 
  and bzero value for each input image are written to the linear
  transformation file <I>lintransform</I>.
  If <I>databasefmt</I> is "<TT>yes</TT>" each result is written to a record whose name
  is either identical to the name of the input
  image or supplied by the user via the <I>records</I> parameter .
  If <I>databasefmt</I> is "<TT>no</TT>", then a single line containing the input image
  name and the computed bscale and bzero values and their errors
  is written to the output shifts file.
  <P>
  If a list of output image names have been supplied then the bscale and
  bzero values will be applied to the input images to compute the output images.
  <P>
  If the <I>scaling</I> parameter is set to "<TT>file</TT>" then the shifts
  computed in a previous run of LINMATCH will be read from the <I>lintransform</I>
  file and applied to the input images to compute the output images.
  If no record list is supplied by the user LINMATCH will
  search for a record whose name is the same as the input image name. If more than
  one record of the same name is found then the most recently written
  record will be used.
  <P>
  In non-interactive mode the task parameters are set at task startup time
  and the input images are processed sequentially. If the <I>verbose</I>
  flag is set, messages about the progress of the task are printed on the
  screen as the task is running.
  <P>
  In interactive mode the user can mark the regions to be used
  to compute the matching function on the image display, show/set the data
  and algorithm parameters, compute, recompute,  and plot 
  matching function, and interactively delete and undelete
  bad data from the fits using the plots and graphics cursor. A summary
  of the available interactive commands is given in the CURSOR COMMANDS
  section.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Cursor commands</H3>
  <! BeginSection: 'CURSOR COMMANDS'>
  <UL>
  <P>
  <PRE>
  The following graphics cursor commands are currently available in LINMATCH.
  <P>
  		Interactive Keystroke Commands
  <P>
  ?	Print help 
  :	Colon commands
  <P>
  g	Draw a plot of the current fit
  i	Draw the residuals plot for the current fit
  p	Draw a plot of current photometry
  s	Draw histograms for the image region nearest the cursor
  l	Draw the least squares fit for the image region nearest the cursor 
  h	Draw histogram plot of each image region in turn
  l	Draw least squares fits plot of each image region in turn
  r	Redraw the current plot
  d	Delete the image region nearest the cursor
  u	Undelete the image region nearest the cursor
  f	Recompute the intensity matching function
  w	Update the task parameters
  q	Exit
  <P>
  <P>
  		Colon Commands
  <P>
  :markcoords	    Mark objects on the display
  :marksections	    Mark image sections on the display
  :show	            Show current values of all the parameters
  <P>
  		Show/set Parameters
  <P>
  :input		[string]    Show/set the current input image
  :reference	[string]    Show/set the current reference image / phot file 
  :regions	[string]    Show/set the current image regions
  :photfile	[string]    Show/set the current input photometry file
  :lintransform	[string]    Show/set the linear transform database file name
  :dnx		[value]	    Show/set the default x size of an image region
  :dny		[value]	    Show/set the default y size of an image region
  :shifts		[string]    Show/set the current shifts file
  :xshift		[value]     Show/set the input image x shift
  :yshift		[value]     Show/set the input image y shift
  :output		[string]    Show/set the current output image name
  :maxnregions		    Show the maximum number of objects / regions
  :gain		[string]    Show/set the gain value / image header keyword
  :readnoise	[string]    Show/set the readout noise value / image header
                              keyword
  <P>
  :scaling		    Show the current scaling algorithm
  :datamin	[value]     Show/set the minimum good data value
  :datamax	[value]     Show/set the maximum good data value
  :nreject	[value]	    Show/set the maximum number of rejection cycles
  :loreject	[value]     Show/set low side k-sigma rejection parameter
  :hireject	[value]     Show/set high side k-sigma rejection parameter
  </PRE>
  <P>
  </UL>
  <! EndSection:   'CURSOR COMMANDS'>
  <H3>Algorithms</H3>
  <! BeginSection: 'ALGORITHMS'>
  <UL>
  <P>
  MEAN, MEDIAN, AND MODE
  <P>
  For each input and reference image region the mean, median, mode, statistic
  and an error estimate for that statistic are computed as shown below,
  mstat is for mean, median, or mode statistic, emstat stands for the error
  estimate, stdev for the measured standard deviation, and npix for the
  number of points.
  <P>
  <PRE>
         mstat = mean, median, or mode 
        emstat = min (sqrt (mean / gain + readnoise ** 2 / gain ** 2),
                 stdev / sqrt(npix))
  </PRE>
  <P>
  If only a single image region is specified then mstat is used to compute
  one of bscale or bzero but not both as shown below.  Bscale is computed by
  default.
  <P>
  <PRE>
           bscale = mstat[ref] / mstat[input]
      err[bscale] = abs (bscale) * sqrt (emstat[ref] ** 2 / mstat[ref] ** 2 +
  	          emstat[input] ** 2 / mstat[input] ** 2)
  	  bzero = constant
       err[bzero] = 0.0
  <P>
  	  bzero = mstat[ref] - mstat[input]
       err[bzero] = sqrt (emstat[ref] ** 2 + emstat[input] ** 2)
  	 bscale = constant
      err[bscale] = 0.0
  </PRE>
  <P>
  If more than one image region is defined then the computed mean, median,
  or mode values for the input and reference image regions are used as
  shown below to compute the bscale and bzero factors and their errors
  using a weighted least squares fit.
  <P>
  <PRE>
  	mstat[ref] = bscale * mstat[input] + bzero
  </PRE>
  <P>
  If an image region contains data outside the limits defined
  by <I>datamin</I> and <I>datamax</I> that image region is eliminated
  entirely from the fit.
  <P>
  The parameters <I>nreject</I>, <I>loreject</I>,
  and <I>hireject</I> are used to detect and automatically eliminate
  deviant data points from the final least squares fit. If for some reason
  bscale or bzero cannot be fit, default values of 1.0 and 0.0 are
  assigned.
  <P>
  The mean, median, and mode algorithms depend on the global properties of
  the image regions. These algorithms do require the reference and
  input images to have the same pixel scale and orientation,
  but do not automatically require the reference and input images
  to have the same point spread function. Small shifts between the reference
  and input images can be removed using the <I>shifts</I>, <I>xshift</I>, and
  <I>yshift</I> parameters.
  <P>
  If the image regions contain stars, then either regions should be large
  enough to include all the flux of the stars in which case the images
  do not have to have the same psf, or the psfs should be the same so
  that same portion of the psf is sampled. The best image regions for
  matching will contain object and background information.
  <P>
  FIT
  <P>
  For each input and reference image the bscale and bzero factors are
  computed by doing a pixel to pixel weighted least squares fit of the reference
  image counts to the input image counts as shown below.
  <P>
  <PRE>
      counts[ref] = bscale * counts[input] + bzero
           weight = 1.0 / (err[ref] ** 2 + bscale ** 2 * err[input] ** 2)
         err[ref] = sqrt (counts[ref] / gain[ref] + readnoise[ref] ** 2 /
                    gain[ref] ** 2)
       err[input] = sqrt (counts[input] / gain[input] +
       		  readnoise[input] ** 2 / gain[input] ** 2)
  </PRE>
  <P>
  The fitting technique takes into account errors in both the reference and
  input image counts and provides an error estimate for the computed bscale
  and bzero factors. Bad data are rejected
  automatically from the fit by setting the <I>datamin</I> and <I>datamax</I>
  parameters. Deviant pixels are rejected from the fit by setting the
  <I>nreject</I>, <I>loreject</I>, and <I>hireject</I> parameters appropriately.
  <P>
  The final bscale and bzero for the input image are computed by calculating
  the average weighted by their errors  of the individual bscale and bzero
  values. The parameters <I>nreject</I>, <I>loreject</I>, and <I>hirject</I>
  can be used to automatically detect and reject deviant points.
  <P>
  The fit algorithm depends on the results of pixel to pixel fits in 
  each reference and input image region. The technique requires that the
  images be spatially registered and psfmatched before it is employed.
  Each input and reference image should contain a range of pixel intensities
  so that both bscale and bzero can be accurately determined.
  <P>
  PHOTOMETRY
  <P>
  For each object common to the reference and input photometry files
  the input sky values sky, errors in the sky values serr,
  magnitudes mag, and magnitude errors merr are used to compute the 
  bscale and bzero factors and estimate their errors as shown
  below.
  <P>
  <PRE>
  	 bscale = 10.0 ** ((mag[ref] - mag[input]) / 2.5)
  	  bzero = sky[ref] - bscale * sky[input]
      err[bscale] = 0.4 * log(10.0) * bscale * sqrt (merr[ref] ** 2 +
  		  magerr[input] ** 2)) 
       err[bzero] = sqrt (serr[ref] ** 2 + err[bscale] ** 2 *
                    sky[input] ** 2 + bscale ** 2 * sky[input] ** 2)
  </PRE>
  <P>
  The final bscale and bzero for the input image are computed by calculation
  the average of the individual bscale and bzero values weighted by their
  errors. The parameters <I>nreject</I>, <I>loreject</I>, and <I>hirject</I> can
  be used to automatically detect and reject deviant points.
  <P>
  THE LEAST SQUARES FITTING TECHNIQUE
  <P>
  The least squares fitting code performs a double linear regression on
  the x and y points,  taking into account the errors in both x and y.
  <P>
  The best fitting line is the defined below.
  <P>
  <PRE>
  		y = a * x + b
  </PRE>
  <P>
  The error ellipses  are 
  <P>
  <PRE>
  	S = (x - xfit) ** 2 / err[x] ** 2 + (y - yfit) ** 2 /
  	    err[y] ** 2   
  </PRE>
  <P>
  where S is the quantity to be minimized. Initial values of a and b are
  estimated by  fitting the data to a straight line assuming uniform
  weighting.  The best fit values of a and b are then
  determined by iterating on the relationship
  <P>
  <PRE>
  	dy = x' * da + db
  </PRE>
  <P>
  where da and db are corrections to the previously determined values of a and
  b and dy and x' are defined as.
  <P>
  <PRE>
  	dy = y - (ax + b)
  	x' = x + a * err[x] ** 2 * dy / (a ** 2 * err[x] ** 2 +
  	     err[y] ** 2) 
  </PRE>
  <P>
  The new values of the a and b then become.
  <P>
  <PRE>
          a = a + da
  	b = b + db
  </PRE>
  <P>
  </UL>
  <! EndSection:   'ALGORITHMS'>
  <H3>References</H3>
  <! BeginSection: 'REFERENCES'>
  <UL>
  <P>
  A review of doubly weighted linear regression problems in
  astronomy can be found in the paper "<TT>Linear Regression in Astronomy. II</TT>"
  by (Feigelson and Babu (1992 Ap.J. 397, 55). A detailed derivation of the
  particular solution used by LINMATCH can be found in the article
  "<TT>The Techniques of Least Squares and Stellar Photometry with CCDs</TT>"
  by Stetson (1989 Proceeding of the V Advanced School of Astrophysics,
  p 51).
  <P>
  </UL>
  <! EndSection:   'REFERENCES'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Match the intensity scales of a list of images to a reference
  image using a list of stars on the displayed reference image with
  the image cursor and the "<TT>mean</TT>" scaling algorithm. Assume that none
  of the stars are saturated and that a radius of 31 pixels is sufficient
  to include all the flux from the stars plus some background flux.
  Make sure that the correct gain and readout noise values are in the
  image headers.
  <P>
  <PRE>
  	cl&gt; display refimage 1 
  <P>
  	cl&gt; rimcursor &gt; objlist
  	    ... mark several candidate stars by moving the cursor to the
  	        star of interest and hitting the space bar key
  	    ... type EOF to terminate the list
  <P>
  	cl&gt; linmatch @imlist refimage objlist lintran.db \<BR>
  	    out=@outlist dnx=31 dny=31 scaling="mean mean" gain=gain \<BR>
  	    readnoise=readnoise
  </PRE>
  <P>
  2. Repeat the previous command but force the bzero factor to be -100.0
  instead of using the fitted value.
  <P>
  <PRE>
  	cl&gt; linmatch @imlist refimage objlist lintran.db \<BR>
  	    out=@outlist dnx=31 dny=31 scaling="mean -100.0" \<BR>
  	    gain=gain readnoise=rdnoise
  </PRE>
  <P>
  3. Repeat the first example but compute bscale and bzero 
  the bscale and bzero values using boxcar smoothed versions of 
  the input images. Make sure the gain and readout noise are
  adjusted appropriately.
  <P>
  <PRE>
  	cl&gt; linmatch @bimlist brefimage objlist lintran.db \<BR>
  	    dnx=31 dny=31 scaling="mean mean" gain=gain \<BR>
  	    readnoise=rdnoise
  <P>
  	cl&gt; linmatch @imlist refimage objlist lintran.db \<BR>
  	    out=@outimlist records=@bimlist scaling="file file"
  </PRE>
  <P>
  4. Match the intensity of an input image which has been spatially
  registered and psfmatched to the reference image using the "<TT>fit</TT>" algorithm
  and a single reference image region. Remove the effects of saturated
  pixels by setting datamax to 28000 counts, and the effects of any deviant pixels
  by setting nreject, loreject, and hireject to appropriate values.
  <P>
  <PRE>
  	cl&gt; linmatch image refimage [50:150,50:150] lintran.db \<BR>
  	    out=outimage scaling="fit fit" datamax=28000 nreject=3 \<BR>
  	    loreject=3 hireject=3 gain=gain readnoise=rdnoise
  </PRE>
  <P>
  5. Repeat the previous example but use several image sections to compute
  the bscale and bzero values.
  <P>
  <PRE>
  	cl&gt; linmatch image refimage sections lintran.db \<BR>
  	    out=outimage scaling="fit fit" datamax=28000 nreject=3 \<BR>
  	    loreject=3 hireject=3 gain=gain readnoise=rdnoise
  </PRE>
  <P>
  6. Match the intensity scales of two images using photometry 
  computed with the apphot package qphot task. The two images are
  spatially registered, psfmatched, and the photometry aperture is sufficient to
  include all the light from the stars. The filecalc task used to compute
  the error in the mean sky is in the addon ctio package.
  <P>
  <PRE>
  	cl&gt; display refimage 1 fi+
  	cl&gt; rimcursor &gt; objlist
  	    ... mark several candidate stars by moving the cursor to the
  	        star of interest and hitting the space bar key
  	    ... type EOF to terminate the list
  	cl&gt; qphot refimage coords=objlist inter-
  	cl&gt; qphot image coords=objlist inter-
  	cl&gt; pdump refimage.mag.1 msky,stdev,nsky,mag,merr yes | filecalc \<BR>
  	    STDIN "$1;$2/sqrt($3);$4;$5" &gt; refimage.phot
  	cl&gt; pdump image.mag.1 msky,stdev,nsky,mag,merr yes | filecalc \<BR>
  	    STDIN "$1;$2/sqrt($3);$4;$5" &gt; image.phot
  	cl&gt; linmatch image refimage.phot image.phot lintran.db \<BR>
  	    out=outimage scaling="phot phot" nreject=3 loreject=3\<BR>
  	    hireject=3
  </PRE>
  <P>
  7. Register two images interactively using the fit algorithms and
  five non-overlapping image regions in the sections file.
  <P>
  <PRE>
  	cl&gt; linmatch image refimage sections lintran.db \<BR>
  	    out=outimage scaling="fit fit" datamax=28000 nreject=3 \<BR>
  	    loreject=3 hireject=3 gain=gain readnoise=rdnoise \<BR>
  	    interactive +
  <P>
  	    ... a plot of bscale and bzero versus region number
  		appears
  <P>
  	    ... type ? to get a list of the keystroke and : commands
  <P>
  	    ... type i to see a plot of the bscale and bzero residuals
  		versus region
  <P>
  	    ... type g to return to the default bscale and bzero versus
  		region plot
  <P>
  	    ... type l to examine plot of the fits and residuals for the
  		individual regions
  		... step forward and back in the regions list with the
  		space bar and -keys
  		... flip back and forth between the fit and residuals
  		keys with l and i keys
  		... return to the main plot by typing q
  <P>
  	    ... return to the residuals plot by typing i and delete a
  		region with a large residual by moving to the
  		bad point and typing d
  <P>
  	    ... type f to recompute the fit
  <P>
  	    ... type q to quit the interactive loop, n to go to the
  		next image or q to quit the task
  		
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
  imexpr, imcombine, ctio.filecalc, apphot.qphot, apphot.phot
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
