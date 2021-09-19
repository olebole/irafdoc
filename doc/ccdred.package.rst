.. _package:

package: CCD image reduction package
====================================

**Package: ccdred**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  ccdred -- CCD image reduction package
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  ccdred
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>pixeltype = <tt>"real real"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pixeltype' Line='pixeltype = "real real"' -->
  <dd>Output pixel datatype and calculation datatype.  When images are processed
  or created the output pixel datatype is determined by this parameter if the
  specified datatype is of equal or higher precision otherwise the input
  image datatype is preserved.  For example if the output datatype is
  specified as <tt>"input"</tt> then input images which are <tt>"short"</tt> or <tt>"ushort"</tt> will
  be output as integer but any real datatype input images will remain real.
  The allowed types and order of precision are <tt>"short"</tt>, <tt>"ushort"</tt>, <tt>"int"</tt>,
  <tt>"long"</tt>, <tt>"real"</tt>, or <tt>"double"</tt>, for short signed integer, short unsigned
  integer, integer, long integers, and real or double floating point.  Note
  that if short input images are processed into real images the disk space
  required will generally increase.  The calculation datatypes may only be
  short and real with a default of real if none is specified.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>Print log information to the standard output?
  </dd>
  </dl>
  <dl>
  <dt><b>logfile = <tt>"logfile"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "logfile"' -->
  <dd>Text log file.  If no filename is specified then no log file is kept.
  </dd>
  </dl>
  <dl>
  <dt><b>plotfile = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = ""' -->
  <dd>Log metacode plot file for the overscan bias vector fits.  If no filename
  is specified then no metacode plot file is kept.
  </dd>
  </dl>
  <dl>
  <dt><b>backup = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='backup' Line='backup = ""' -->
  <dd>Backup prefix for backup images.  If no prefix is specified then no backup
  images are kept when processing.  If specified then the backup image
  has the specified prefix.
  </dd>
  </dl>
  <dl>
  <dt><b>instrument = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='instrument' Line='instrument = ""' -->
  <dd>CCD instrument translation file.  This is usually set with
  <b>setinstrument</b>.
  </dd>
  </dl>
  <dl>
  <dt><b>ssfile = <tt>"subsets"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ssfile' Line='ssfile = "subsets"' -->
  <dd>Subset translation file used to define the subset identifier.  See
  <b>subsets</b> for more.
  </dd>
  </dl>
  <dl>
  <dt><b>graphics = <tt>"stdgraph"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"' -->
  <dd>Interactive graphics output device when fitting the overscan bias vector.
  </dd>
  </dl>
  <dl>
  <dt><b>cursor = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""' -->
  <dd>Graphics cursor input.  The default is the standard graphics cursor.
  </dd>
  </dl>
  <dl>
  <dt><b>version = <tt>"June 1987"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='version' Line='version = "June 1987"' -->
  <dd>Package version.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The CCD reduction package is loaded when this command is entered.  The
  package contains parameters which affect the operation of the tasks it
  defines.  When images are processed or new image are created the output
  pixel datatype is that specified by the parameter <b>pixeltype</b>.  Note
  that CCD processing replaces the original image by the processed image so
  the pixel type of the CCD images may change during processing.  The output
  pixel type is not allowed to change to a lower precision but it is common
  for input short images to be processed to real images.  Processing images
  from short to real pixel datatypes will generally increase the amount of
  disk space required (a factor of 2 on most computers).
  </p>
  <p>
  The tasks produce log output which may be printed on the standard
  output (the terminal unless redirected) and appended to a file.  The
  parameter <i>verbose</i> determines whether processing information
  is printed.  This may be desirable initially, but when using background
  jobs the verbose output should be turned off.  The user may look at
  the end of the log file (for example with <b>tail</b>) to determine
  the status of the processing.
  </p>
  <p>
  The package was designed to work with data from many different observatories
  and instruments.  In order to accomplish this an instrument translation
  file is used to define a mapping between the package parameters and
  the particular image header format.  The instrument translation file
  is specified to the package by the parameter <i>instrument</i>.  This
  parameter is generally set by the task <b>setinstrument</b>.  The other
  file used is a subset file.  This is generally created and maintained
  by the package and the user need not do anything.  For more sophisticated
  users see <b>instruments</b> and <b>subsets</b>.
  </p>
  <p>
  The package has very little graphics
  output.  The exception is the overscan bias subtraction.  The bias
  vector is logged in the metacode plot file if given.  The plot file
  may be examined with the tasks in the <b>plot</b> package such as
  <b>gkimosaic</b>.  When interactively fitting the overscan vector
  the graphics input and output devices must be specified.  The defaults
  should apply in most cases.
  </p>
  <p>
  Because processing replaces the input image by the processed image it
  may be desired to save the original image.  This may be done by
  specifying a backup prefix with the parameter <i>backup</i>.  For
  example, if the prefix is <tt>"orig"</tt> and the image is <tt>"ccd001"</tt>, the backup
  image will be <tt>"origccd001"</tt>.  The prefix may be a directory but it must
  end with <tt>'/'</tt> or <tt>'$'</tt> (for logical directories).
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  ccdproc, instruments, setinstrument, subsets
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'SEE ALSO'  -->
  
