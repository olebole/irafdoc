.. _linmatch:

linmatch: Match the linear intensity scales of 1-D or 2-D images
================================================================

**Package: immatch**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  linmatch -- linearly match the intensity scales of 1 and 2D images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  linmatch input reference regions lintransform
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The list of input images to be matched.
  </dd>
  </dl>
  <dl>
  <dt><b>reference</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='reference' Line='reference' -->
  <dd>The list of reference images to which the input images are to be matched
  if <i>scaling</i>  is one of the <tt>"mean"</tt>, <tt>"median"</tt>, <tt>"mode"</tt>, or <tt>"fit"</tt>
  algorithms, or the list of reference photometry files if <i>scaling</i>
  specifies the <tt>"photometry"</tt> algorithm. The number of reference images or
  reference photometry files must be one or equal to the number of input
  images.
  </dd>
  </dl>
  <dl>
  <dt><b>regions</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='regions' Line='regions' -->
  <dd>The list of image regions used to compute the intensity 
  matching function if <i>scaling</i> is one of the <tt>"mean"</tt>, <tt>"median"</tt>, <tt>"mode"</tt>,
  or <tt>"fit"</tt> algorithms, or a list of the input photometry files if
  <i>scaling</i> specifies the <tt>"photometry"</tt> algorithm. In the former
  case <i>regions</i> may be: 1) a string of the form <tt>"grid nx ny"</tt> defining
  a grid of nx by ny equally spaced and sized image regions spanning the
  entire image, 2) a list of object coordinates separated by commas e.g.
  <tt>"303 401, 131 202"</tt>, 3) a list of image sections separated by whitespace
  e.g <tt>"[101:200,101:200] [301:400,301:400]"</tt>,
  4) the name of a text file containing a list of object coordinates separated
  by newlines, and 5) the name of a text file containing a list of image
  sections separated by whitespace and/or newlines.
  </dd>
  </dl>
  <dl>
  <dt><b>lintransform</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='lintransform' Line='lintransform' -->
  <dd>The name of the text file where the computed scaling factors are written.
  If <i>databasefmt</i> is <tt>"yes"</tt>, a single record containing the computed
  bscale and bzero factors for each image region or object, and the
  average bscale and bzero, is written to the text database
  file for each input image. If <i>databasefmt</i> = <tt>"no"</tt>, a single line
  containing the input image name, bscale factor, bzero factor, error
  in bscale, and error in bzero is written to a simple text file for
  each image.
  </dd>
  </dl>
  <dl>
  <dt><b>output = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output = ""' -->
  <dd>The list of output matched images. If <i>output</i> is the NULL string
  then bscale  and bzero are computed for each input image and written to
  <i>lintransform</i>, but no output images are written. If <i>output</i>
  is not NULL then the number of output images must equal the number of
  input images.
  </dd>
  </dl>
  <dl>
  <dt><b>databasefmt = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='databasefmt' Line='databasefmt = yes' -->
  <dd>If <i>databasefmt</i> is <tt>"yes"</tt> the computed bscale and bzero factors
  are written to a text database file, otherwise they are written to a
  simple text file.
  </dd>
  </dl>
  <dl>
  <dt><b>records = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='records' Line='records = ""' -->
  <dd>The list of records to be written to or read from <i>lintransform</i> one
  input image. If <i>records</i> is NULL then the output or input record names
  are assumed to be the names of the input images. If <i>records</i> is not NULL
  then the record names in <i>records</i> are used to write / read the
  database records. This parameter is useful for users
  who, wish to compute the bscale and bzero factors using images that have
  been processed
  in some manner (e.g. smoothed), but apply the computed bscale and bzero
  factors to the original unprocessed images. If more than one record
  with the same name exists in <i>lintransform</i> then the most recently written
  record takes precedence. The records parameter is ignored if
  <i>databasefmt</i> is <tt>"no"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>append = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='append' Line='append = yes' -->
  <dd>Append new records to an existing <i>lintransform</i> file or start a new 
  file for each execution of LINMATCH? The append parameter is
  ignored if <i>databasefmt</i> is <tt>"no"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>shifts = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='shifts' Line='shifts = ""' -->
  <dd>An optional list of shifts files containing the x and y shifts to be applied
  to the reference regions to determine their positions in
  the input images. The number of shifts files must equal the number of
  reference images. The shifts are listed in the shifts file, 1 shift per line,
  with the x and y shifts in
  columns 1 and 2 respectively. If there are fewer x and y shifts defined
  in the shifts file than there are input images, the extra input
  images will be assigned x and y shifts of <i>xshift</i> and <i>yshift</i>
  respectively. The shifts parameter is ignored if the <i>scaling</i>
  parameter is set to <tt>"photometry"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>xshift = 0.0 yshift = 0.0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='xshift' Line='xshift = 0.0 yshift = 0.0' -->
  <dd>The default x and y shifts to be applied to the reference image regions
  or objects to compute their positions in the input image.
  Values in <i>shifts</i> take precedence over the values of <i>xshift</i> and
  <i>yshift</i>. xshift and yshift are ignored if the <i>scaling</i> parameter
  is set to <tt>"photometry"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>dnx = 31 dny = 31</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='dnx' Line='dnx = 31 dny = 31' -->
  <dd>The default size of a single image region used to compute the bscale
  and bzero factors if <i>scaling</i> is one of the <tt>"mean"</tt>, <tt>"median"</tt>, <tt>"mode"</tt>,
  or <tt>"fit"</tt> algorithms and <i>regions</i> is a coordinate list rather than
  a sections list.  dnx and dny are ignored if the <i>scaling</i> parameter
  is set to <tt>"photometry"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>maxnregions = 100</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='maxnregions' Line='maxnregions = 100' -->
  <dd>The maximum number of image regions or objects with measured photometry
  that can be used to compute the bscale and bzero factors.
  </dd>
  </dl>
  <dl>
  <dt><b>scaling = <tt>"mean mean"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='scaling' Line='scaling = "mean mean"' -->
  <dd>The algorithms used to compute the bscale and bzero factors respectively.
  The options are:
  <dl>
  <dt><b>mean median mode</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='mean' Line='mean median mode' -->
  <dd>Bscale or bzero are computed using the <tt>"mean"</tt>, <tt>"median"</tt>, or <tt>"mode"</tt> statistic
  for each input and reference region individually. If one of the bscale or
  bzero fitting
  algorithms is set to <tt>"mean"</tt>, <tt>"median"</tt>, or <tt>"mode"</tt>, the remaining factor
  must be set to <tt>"mean"</tt>, <tt>"median"</tt> or <tt>"mode"</tt> or  a numerical constant,
  e.g. <tt>"mean mean"</tt>, <tt>"mean -100.0"</tt> or <tt>"2.63 mode"</tt>.
  If both algorithms are set to <tt>"mean"</tt>, <tt>"median"</tt>, or <tt>"mode"</tt> bscale will be
  computed using the specified statistic and bzero will be set to 0.0
  If more than one input region is defined then a weighted least squares
  fit of the reference statistics to the input image statistics  
  is performed and used to compute the final bscale and bzero factors.
  </dd>
  </dl>
  <dl>
  <dt><b>fit    </b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='fit' Line='fit    ' -->
  <dd>Bscale and bzero are computed for each input image region individually
  by performing a least squares fit of the reference image pixels to
  the input image pixels. If more than one input image region is defined
  the final bscale and bzero factors are computed by averaging,
  weighted by their signal-to-noise ratios, the individual bscale and bzero
  values.  If one of the bscale or bzero fitting
  algorithms is set to <tt>"fit"</tt>, the remaining factor must either also
  be computed with the <tt>"fit"</tt> algorithm  or set to a numerical constant,
  e.g. <tt>"fit fit"</tt>, <tt>"fit -100.0"</tt>, or <tt>"2.63 fit"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>photometry</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='photometry' Line='photometry' -->
  <dd>Bscale and/or bzero are computed for each input object individually
  using photometry computed for a set of objects common to the reference
  and input images.  If more than one input object is defined
  the final bscale and bzero factors are computed by averaging,
  weighted by their signal-to-noise ratios, the individual bscale and bzero
  values.  If one of the bscale or bzero fitting
  algorithms is set to <tt>"photometry"</tt>, the remaining factor must either also
  be computed with the <tt>"photometry"</tt> algorithm or set to a numerical
  constant, e.g. <tt>"photometry photometry"</tt>, <tt>"photometry -100.0"</tt>, or
  <tt>"2.63 photometry"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>number</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='number' Line='number' -->
  <dd>Bscale and/or bzero are set to user defined numerical constants,
  e.g. <tt>"2.62 -55.0"</tt> or  <tt>"2.62 median"</tt>. If both bscale and bzero are numerical
  constants, LINMATCH must be run in non-interactive mode. If only one of bscale
  or bzero is a numerical constant, any of the <tt>"mean"</tt>, <tt>"median"</tt>, <tt>"mode"</tt>, <tt>"fit"</tt>,
  or <tt>"photometry"</tt> algorithms may be used to compute the remaining factor.
  </dd>
  </dl>
  <dl>
  <dt><b>file</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='file' Line='file' -->
  <dd>Bscale and bzero are not computed but instead read from record <i>record</i> in
  the text database file <i>lintransform</i> if <i>databasefmt</i> is <tt>"yes"</tt>,
  or the next line of a simple text file if <i>databasefmt</i> is <tt>"no"</tt>.
  </dd>
  </dl>
  Further description of the matching algorithms can be found in the ALGORITHMS
  section.
  </dd>
  </dl>
  <dl>
  <dt><b>datamin = INDEF datamax = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='datamin' Line='datamin = INDEF datamax = INDEF' -->
  <dd>The minimum and maximum good data values. Datamin and datamax are used by
  the <tt>"mean"</tt>, <tt>"median"</tt>, and <tt>"mode"</tt> scaling algorithms to reject entire
  image regions from the final fit, and by the <tt>"fit"</tt> algorithm to reject
  individual bad pixels from the least squares fits for the individual
  regions.
  </dd>
  </dl>
  <dl>
  <dt><b>maxiter = 10</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='maxiter' Line='maxiter = 10' -->
  <dd>The maximum number of iterations performed by the least squares fitting
  algorithm.
  </dd>
  </dl>
  <dl>
  <dt><b>nreject = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nreject' Line='nreject = 0' -->
  <dd>The maximum number of rejection cycles used to detect and reject bad pixels
  from the fit if the scaling algorithm is <tt>"fit"</tt> or bad regions / objects
  from the fit if the scaling algorithm is <tt>"mean"</tt>, <tt>"median"</tt>, <tt>"mode"</tt>, <tt>"fit"</tt>,
  or <tt>"photometry"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>loreject = INDEF hireject = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='loreject' Line='loreject = INDEF hireject = INDEF' -->
  <dd>The high- and low-side bad data rejection limits used to detect and reject
  deviant pixels from the fit if the scaling algorithm is <tt>"fit"</tt> or bad
  regions / objects from the fit if the scaling algorithm is <tt>"mean"</tt>, <tt>"median"</tt>,
  <tt>"mode"</tt>, <tt>"fit"</tt>, or <tt>"photometry"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>gain = <tt>"1.0 1.0"</tt> readnoise = <tt>"0.0 0.0"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='gain' Line='gain = "1.0 1.0" readnoise = "0.0 0.0"' -->
  <dd>The reference and input image gain and readout noise in e-/ADU and
  e- respectively. Gain and readout may be numerical constants or the
  image header keyword containing the actual gain and/or readout noise
  value. Gain and readnoise are used by the <tt>"mean"</tt>, <tt>"median"</tt>, <tt>"mode"</tt>,
  and <tt>"fit"</tt> algorithms to estimate the expected errors in the computed
  <tt>"mean"</tt>, <tt>"median"</tt>, or <tt>"mode"</tt> statistics,  and by the <tt>"fit"</tt> algorithm
  to compute the per pixel errors values.
  </dd>
  </dl>
  <dl>
  <dt><b>interactive = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='interactive' Line='interactive = no' -->
  <dd>Compute the bscale and bzero scaling factors for each image interactively
  using graphics cursor and optionally image cursor input.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print messages about the progress of the task during task execution in
  non-interactive mode.
  </dd>
  </dl>
  <dl>
  <dt><b>graphics = <tt>"stdgraph"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"' -->
  <dd>The default graphics device.
  </dd>
  </dl>
  <dl>
  <dt><b>display = <tt>"stdimage"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='display' Line='display = "stdimage"' -->
  <dd>The default image display device.
  </dd>
  </dl>
  <dl>
  <dt><b>gcommands = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='gcommands' Line='gcommands = ""' -->
  <dd>The default graphics cursor.
  </dd>
  </dl>
  <dl>
  <dt><b>icommands = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='icommands' Line='icommands = ""' -->
  <dd>The default image cursor.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  LINMATCH computes the bscale and bzero factors required to match
  the intensity scales of a list of input
  images <i>input</i> to the intensity scales of a list of reference
  images <i>reference</i> using the following definition of
  bscale and bzero and a variety of techniques.
  </p>
  <pre>
  	reference = bscale * input + bzero
  </pre>
  <p>
  The computed bscale and bzero factors are stored
  in the text file <i>lintransform</i>, in the record <i>records</i> if
  <i>databasefmt</i> is <tt>"yes"</tt>, or a single line of a simple text file
  if <i>databasefmt</i> is <tt>"no"</tt>. One record is written to the output file
  file for each input image. If a non NULL list of output images
  <i>output</i> is supplied, a scaled output image is written for
  each input image. LINMATCH is intended to solve 1D and 2D image intensity
  matching problems where the input and reference images: 1) have the same
  pixel scale and orientation, 2) differ in intensity by at most a scale
  factor and a zero point, and 3) contain one or more regions or objects in
  common that can be used to compute the scaling factors. Some of the scaling
  algorithms also require that the images registered and have identical
  point spread functions. LINMATCH cannot be used to compute or apply non-linear
  intensity matching functions.
  </p>
  <p>
  If <i>scaling</i> = <tt>"mean"</tt>, <tt>"median"</tt>, <tt>"mode"</tt>, or <tt>"fit"</tt> bscale and bzero
  are computed directly from the input and reference image data using the
  image sections specified in the <i>regions</i> and one of the above fitting
  techniques as described in the ALGORITHMS section. All four algorithms
  require accurate knowledge of the measurement errors which in turn
  require accurate knowledge of the input and reference image gain and
  readout noise values. Gain and readout noise values can be entered by
  setting the <i>gain</i> and <i>readnouse</i> parameters to the appropriate
  numerical values or image header keyword.
  </p>
  <p>
  <i>Regions</i> is interpreted as either: 1) a string of
  the form <tt>"grid nx ny"</tt> specifying a list of nx by ny image sections
  spanning the entire image, 2) a string defining the coordinates of a list
  of objects separated by commas e.g.
  <tt>"103.3 189.2, 204.4 389.7"</tt>, 3) a string containing a list of image
  sections separated by whitespace, e.g <tt>"[100:203,200:300] [400:500,400:500]"</tt>
  4) the name of a text file containing the coordinates of one or
  more objects, one object per line, with the x and y coordinates
  in columns 1 and 2 respectively, 5) the name of a text
  file containing a list of image sections separated by whitespace and/or
  newlines.  The image sections specifications, or alternatively
  the object coordinates and the parameters <i>dnx</i> and <i>dny</i>,
  determine the size of the input and reference image data regions to be
  extracted and used to compute the bscale and bzero factors.
  These image regions should be selected with care. Ideal regions
  span a range of intensity values and contain both object and background
  data. 
  </p>
  <p>
  If <i>scaling</i> = <tt>"photometry"</tt>, the bscale and bzero factors
  are computed directly from data in the input and reference image photometry
  files using the technique described in the ALGORITHMS section.
  In this case <i>regions</i> is a list of the input image photometry
  files and <i>reference</i> are the corresponding reference image
  photometry files written by a separate photometry task.
  These photometry files are simple text files with the object
  sky values, errors in the sky values, magnitudes, and errors in the
  magnitudes in columns 1, 2, 3, and 4 respectively.
  </p>
  <p>
  An image region is rejected from the fit if it contains data outside the
  limits specified by the <i>datamin</i> and <i>datamax</i> parameters
  and <i>scaling</i> =
  <tt>"mean"</tt>, <tt>"median"</tt>, or <tt>"mode"</tt>. A pixel is rejected from the fit for an
  individual region if the pixel value is outside the limits specified
  by datamin and datamax, and the scaling algorithm is <tt>"fit"</tt>. The datamin
  and datamax parameters are not used by the <tt>"photometry"</tt> scaling algorithm .
  </p>
  <p>
  Deviant pixels can be rejected from the fits to individual image regions
  if <i>scaling</i> = <tt>"fit"</tt>, and <i>nreject</i>, <i>loreject</i>, and
  <i>hireject</i> are set appropriately. Nreject, loreject and reject
  are also be used by all the scaling algorithms  to reject image regions
  which contribute deviant bscale and bzero values.
  </p>
  <p>
  The computed bscale and bzero value for each region and the final bscale 
  and bzero value for each input image are written to the linear
  transformation file <i>lintransform</i>.
  If <i>databasefmt</i> is <tt>"yes"</tt> each result is written to a record whose name
  is either identical to the name of the input
  image or supplied by the user via the <i>records</i> parameter .
  If <i>databasefmt</i> is <tt>"no"</tt>, then a single line containing the input image
  name and the computed bscale and bzero values and their errors
  is written to the output shifts file.
  </p>
  <p>
  If a list of output image names have been supplied then the bscale and
  bzero values will be applied to the input images to compute the output images.
  </p>
  <p>
  If the <i>scaling</i> parameter is set to <tt>"file"</tt> then the shifts
  computed in a previous run of LINMATCH will be read from the <i>lintransform</i>
  file and applied to the input images to compute the output images.
  If no record list is supplied by the user LINMATCH will
  search for a record whose name is the same as the input image name. If more than
  one record of the same name is found then the most recently written
  record will be used.
  </p>
  <p>
  In non-interactive mode the task parameters are set at task startup time
  and the input images are processed sequentially. If the <i>verbose</i>
  flag is set, messages about the progress of the task are printed on the
  screen as the task is running.
  </p>
  <p>
  In interactive mode the user can mark the regions to be used
  to compute the matching function on the image display, show/set the data
  and algorithm parameters, compute, recompute,  and plot 
  matching function, and interactively delete and undelete
  bad data from the fits using the plots and graphics cursor. A summary
  of the available interactive commands is given in the CURSOR COMMANDS
  section.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Cursor commands</h3>
  <!-- BeginSection: 'CURSOR COMMANDS' -->
  <pre>
  The following graphics cursor commands are currently available in LINMATCH.
  
  		Interactive Keystroke Commands
  
  ?	Print help 
  :	Colon commands
  
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
  
  
  		Colon Commands
  
  :markcoords	    Mark objects on the display
  :marksections	    Mark image sections on the display
  :show	            Show current values of all the parameters
  
  		Show/set Parameters
  
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
  
  :scaling		    Show the current scaling algorithm
  :datamin	[value]     Show/set the minimum good data value
  :datamax	[value]     Show/set the maximum good data value
  :nreject	[value]	    Show/set the maximum number of rejection cycles
  :loreject	[value]     Show/set low side k-sigma rejection parameter
  :hireject	[value]     Show/set high side k-sigma rejection parameter
  </pre>
  <!-- EndSection:   'CURSOR COMMANDS' -->
  <h3>Algorithms</h3>
  <!-- BeginSection: 'ALGORITHMS' -->
  <p>
  MEAN, MEDIAN, AND MODE
  </p>
  <p>
  For each input and reference image region the mean, median, mode, statistic
  and an error estimate for that statistic are computed as shown below,
  mstat is for mean, median, or mode statistic, emstat stands for the error
  estimate, stdev for the measured standard deviation, and npix for the
  number of points.
  </p>
  <pre>
         mstat = mean, median, or mode 
        emstat = min (sqrt (mean / gain + readnoise ** 2 / gain ** 2),
                 stdev / sqrt(npix))
  </pre>
  <p>
  If only a single image region is specified then mstat is used to compute
  one of bscale or bzero but not both as shown below.  Bscale is computed by
  default.
  </p>
  <pre>
           bscale = mstat[ref] / mstat[input]
      err[bscale] = abs (bscale) * sqrt (emstat[ref] ** 2 / mstat[ref] ** 2 +
  	          emstat[input] ** 2 / mstat[input] ** 2)
  	  bzero = constant
       err[bzero] = 0.0
  
  	  bzero = mstat[ref] - mstat[input]
       err[bzero] = sqrt (emstat[ref] ** 2 + emstat[input] ** 2)
  	 bscale = constant
      err[bscale] = 0.0
  </pre>
  <p>
  If more than one image region is defined then the computed mean, median,
  or mode values for the input and reference image regions are used as
  shown below to compute the bscale and bzero factors and their errors
  using a weighted least squares fit.
  </p>
  <pre>
  	mstat[ref] = bscale * mstat[input] + bzero
  </pre>
  <p>
  If an image region contains data outside the limits defined
  by <i>datamin</i> and <i>datamax</i> that image region is eliminated
  entirely from the fit.
  </p>
  <p>
  The parameters <i>nreject</i>, <i>loreject</i>,
  and <i>hireject</i> are used to detect and automatically eliminate
  deviant data points from the final least squares fit. If for some reason
  bscale or bzero cannot be fit, default values of 1.0 and 0.0 are
  assigned.
  </p>
  <p>
  The mean, median, and mode algorithms depend on the global properties of
  the image regions. These algorithms do require the reference and
  input images to have the same pixel scale and orientation,
  but do not automatically require the reference and input images
  to have the same point spread function. Small shifts between the reference
  and input images can be removed using the <i>shifts</i>, <i>xshift</i>, and
  <i>yshift</i> parameters.
  </p>
  <p>
  If the image regions contain stars, then either regions should be large
  enough to include all the flux of the stars in which case the images
  do not have to have the same psf, or the psfs should be the same so
  that same portion of the psf is sampled. The best image regions for
  matching will contain object and background information.
  </p>
  <p>
  FIT
  </p>
  <p>
  For each input and reference image the bscale and bzero factors are
  computed by doing a pixel to pixel weighted least squares fit of the reference
  image counts to the input image counts as shown below.
  </p>
  <pre>
      counts[ref] = bscale * counts[input] + bzero
           weight = 1.0 / (err[ref] ** 2 + bscale ** 2 * err[input] ** 2)
         err[ref] = sqrt (counts[ref] / gain[ref] + readnoise[ref] ** 2 /
                    gain[ref] ** 2)
       err[input] = sqrt (counts[input] / gain[input] +
       		  readnoise[input] ** 2 / gain[input] ** 2)
  </pre>
  <p>
  The fitting technique takes into account errors in both the reference and
  input image counts and provides an error estimate for the computed bscale
  and bzero factors. Bad data are rejected
  automatically from the fit by setting the <i>datamin</i> and <i>datamax</i>
  parameters. Deviant pixels are rejected from the fit by setting the
  <i>nreject</i>, <i>loreject</i>, and <i>hireject</i> parameters appropriately.
  </p>
  <p>
  The final bscale and bzero for the input image are computed by calculating
  the average weighted by their errors  of the individual bscale and bzero
  values. The parameters <i>nreject</i>, <i>loreject</i>, and <i>hirject</i>
  can be used to automatically detect and reject deviant points.
  </p>
  <p>
  The fit algorithm depends on the results of pixel to pixel fits in 
  each reference and input image region. The technique requires that the
  images be spatially registered and psfmatched before it is employed.
  Each input and reference image should contain a range of pixel intensities
  so that both bscale and bzero can be accurately determined.
  </p>
  <p>
  PHOTOMETRY
  </p>
  <p>
  For each object common to the reference and input photometry files
  the input sky values sky, errors in the sky values serr,
  magnitudes mag, and magnitude errors merr are used to compute the 
  bscale and bzero factors and estimate their errors as shown
  below.
  </p>
  <pre>
  	 bscale = 10.0 ** ((mag[ref] - mag[input]) / 2.5)
  	  bzero = sky[ref] - bscale * sky[input]
      err[bscale] = 0.4 * log(10.0) * bscale * sqrt (merr[ref] ** 2 +
  		  magerr[input] ** 2)) 
       err[bzero] = sqrt (serr[ref] ** 2 + err[bscale] ** 2 *
                    sky[input] ** 2 + bscale ** 2 * sky[input] ** 2)
  </pre>
  <p>
  The final bscale and bzero for the input image are computed by calculation
  the average of the individual bscale and bzero values weighted by their
  errors. The parameters <i>nreject</i>, <i>loreject</i>, and <i>hirject</i> can
  be used to automatically detect and reject deviant points.
  </p>
  <p>
  THE LEAST SQUARES FITTING TECHNIQUE
  </p>
  <p>
  The least squares fitting code performs a double linear regression on
  the x and y points,  taking into account the errors in both x and y.
  </p>
  <p>
  The best fitting line is the defined below.
  </p>
  <pre>
  		y = a * x + b
  </pre>
  <p>
  The error ellipses  are 
  </p>
  <pre>
  	S = (x - xfit) ** 2 / err[x] ** 2 + (y - yfit) ** 2 /
  	    err[y] ** 2   
  </pre>
  <p>
  where S is the quantity to be minimized. Initial values of a and b are
  estimated by  fitting the data to a straight line assuming uniform
  weighting.  The best fit values of a and b are then
  determined by iterating on the relationship
  </p>
  <pre>
  	dy = x' * da + db
  </pre>
  <p>
  where da and db are corrections to the previously determined values of a and
  b and dy and x' are defined as.
  </p>
  <pre>
  	dy = y - (ax + b)
  	x' = x + a * err[x] ** 2 * dy / (a ** 2 * err[x] ** 2 +
  	     err[y] ** 2) 
  </pre>
  <p>
  The new values of the a and b then become.
  </p>
  <pre>
          a = a + da
  	b = b + db
  </pre>
  <!-- EndSection:   'ALGORITHMS' -->
  <h3>References</h3>
  <!-- BeginSection: 'REFERENCES' -->
  <p>
  A review of doubly weighted linear regression problems in
  astronomy can be found in the paper <tt>"Linear Regression in Astronomy. II"</tt>
  by (Feigelson and Babu (1992 Ap.J. 397, 55). A detailed derivation of the
  particular solution used by LINMATCH can be found in the article
  <tt>"The Techniques of Least Squares and Stellar Photometry with CCDs"</tt>
  by Stetson (1989 Proceeding of the V Advanced School of Astrophysics,
  p 51).
  </p>
  <!-- EndSection:   'REFERENCES' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Match the intensity scales of a list of images to a reference
  image using a list of stars on the displayed reference image with
  the image cursor and the <tt>"mean"</tt> scaling algorithm. Assume that none
  of the stars are saturated and that a radius of 31 pixels is sufficient
  to include all the flux from the stars plus some background flux.
  Make sure that the correct gain and readout noise values are in the
  image headers.
  </p>
  <pre>
  	cl&gt; display refimage 1 
  
  	cl&gt; rimcursor &gt; objlist
  	    ... mark several candidate stars by moving the cursor to the
  	        star of interest and hitting the space bar key
  	    ... type EOF to terminate the list
  
  	cl&gt; linmatch @imlist refimage objlist lintran.db \<br>
  	    out=@outlist dnx=31 dny=31 scaling="mean mean" gain=gain \<br>
  	    readnoise=readnoise
  </pre>
  <p>
  2. Repeat the previous command but force the bzero factor to be -100.0
  instead of using the fitted value.
  </p>
  <pre>
  	cl&gt; linmatch @imlist refimage objlist lintran.db \<br>
  	    out=@outlist dnx=31 dny=31 scaling="mean -100.0" \<br>
  	    gain=gain readnoise=rdnoise
  </pre>
  <p>
  3. Repeat the first example but compute bscale and bzero 
  the bscale and bzero values using boxcar smoothed versions of 
  the input images. Make sure the gain and readout noise are
  adjusted appropriately.
  </p>
  <pre>
  	cl&gt; linmatch @bimlist brefimage objlist lintran.db \<br>
  	    dnx=31 dny=31 scaling="mean mean" gain=gain \<br>
  	    readnoise=rdnoise
  
  	cl&gt; linmatch @imlist refimage objlist lintran.db \<br>
  	    out=@outimlist records=@bimlist scaling="file file"
  </pre>
  <p>
  4. Match the intensity of an input image which has been spatially
  registered and psfmatched to the reference image using the <tt>"fit"</tt> algorithm
  and a single reference image region. Remove the effects of saturated
  pixels by setting datamax to 28000 counts, and the effects of any deviant pixels
  by setting nreject, loreject, and hireject to appropriate values.
  </p>
  <pre>
  	cl&gt; linmatch image refimage [50:150,50:150] lintran.db \<br>
  	    out=outimage scaling="fit fit" datamax=28000 nreject=3 \<br>
  	    loreject=3 hireject=3 gain=gain readnoise=rdnoise
  </pre>
  <p>
  5. Repeat the previous example but use several image sections to compute
  the bscale and bzero values.
  </p>
  <pre>
  	cl&gt; linmatch image refimage sections lintran.db \<br>
  	    out=outimage scaling="fit fit" datamax=28000 nreject=3 \<br>
  	    loreject=3 hireject=3 gain=gain readnoise=rdnoise
  </pre>
  <p>
  6. Match the intensity scales of two images using photometry 
  computed with the apphot package qphot task. The two images are
  spatially registered, psfmatched, and the photometry aperture is sufficient to
  include all the light from the stars. The filecalc task used to compute
  the error in the mean sky is in the addon ctio package.
  </p>
  <pre>
  	cl&gt; display refimage 1 fi+
  	cl&gt; rimcursor &gt; objlist
  	    ... mark several candidate stars by moving the cursor to the
  	        star of interest and hitting the space bar key
  	    ... type EOF to terminate the list
  	cl&gt; qphot refimage coords=objlist inter-
  	cl&gt; qphot image coords=objlist inter-
  	cl&gt; pdump refimage.mag.1 msky,stdev,nsky,mag,merr yes | filecalc \<br>
  	    STDIN "$1;$2/sqrt($3);$4;$5" &gt; refimage.phot
  	cl&gt; pdump image.mag.1 msky,stdev,nsky,mag,merr yes | filecalc \<br>
  	    STDIN "$1;$2/sqrt($3);$4;$5" &gt; image.phot
  	cl&gt; linmatch image refimage.phot image.phot lintran.db \<br>
  	    out=outimage scaling="phot phot" nreject=3 loreject=3\<br>
  	    hireject=3
  </pre>
  <p>
  7. Register two images interactively using the fit algorithms and
  five non-overlapping image regions in the sections file.
  </p>
  <pre>
  	cl&gt; linmatch image refimage sections lintran.db \<br>
  	    out=outimage scaling="fit fit" datamax=28000 nreject=3 \<br>
  	    loreject=3 hireject=3 gain=gain readnoise=rdnoise \<br>
  	    interactive +
  
  	    ... a plot of bscale and bzero versus region number
  		appears
  
  	    ... type ? to get a list of the keystroke and : commands
  
  	    ... type i to see a plot of the bscale and bzero residuals
  		versus region
  
  	    ... type g to return to the default bscale and bzero versus
  		region plot
  
  	    ... type l to examine plot of the fits and residuals for the
  		individual regions
  		... step forward and back in the regions list with the
  		space bar and -keys
  		... flip back and forth between the fit and residuals
  		keys with l and i keys
  		... return to the main plot by typing q
  
  	    ... return to the residuals plot by typing i and delete a
  		region with a large residual by moving to the
  		bad point and typing d
  
  	    ... type f to recompute the fit
  
  	    ... type q to quit the interactive loop, n to go to the
  		next image or q to quit the task
  		
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imexpr, imcombine, ctio.filecalc, apphot.qphot, apphot.phot
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'CURSOR COMMANDS' 'ALGORITHMS' 'REFERENCES' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
