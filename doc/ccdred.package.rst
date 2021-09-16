.. _package:

package — CCD image reduction package
=====================================

**Package: ccdred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  ccdred -- CCD image reduction package
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  ccdred
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>pixeltype = "<TT>real real</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixeltype' Line='pixeltype = "real real"'>
  <DD>Output pixel datatype and calculation datatype.  When images are processed
  or created the output pixel datatype is determined by this parameter if the
  specified datatype is of equal or higher precision otherwise the input
  image datatype is preserved.  For example if the output datatype is
  specified as "<TT>input</TT>" then input images which are "<TT>short</TT>" or "<TT>ushort</TT>" will
  be output as integer but any real datatype input images will remain real.
  The allowed types and order of precision are "<TT>short</TT>", "<TT>ushort</TT>", "<TT>int</TT>",
  "<TT>long</TT>", "<TT>real</TT>", or "<TT>double</TT>", for short signed integer, short unsigned
  integer, integer, long integers, and real or double floating point.  Note
  that if short input images are processed into real images the disk space
  required will generally increase.  The calculation datatypes may only be
  short and real with a default of real if none is specified.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print log information to the standard output?
  </DD>
  </DL>
  <DL>
  <DT><B>logfile = "<TT>logfile</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfile' Line='logfile = "logfile"'>
  <DD>Text log file.  If no filename is specified then no log file is kept.
  </DD>
  </DL>
  <DL>
  <DT><B>plotfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='plotfile' Line='plotfile = ""'>
  <DD>Log metacode plot file for the overscan bias vector fits.  If no filename
  is specified then no metacode plot file is kept.
  </DD>
  </DL>
  <DL>
  <DT><B>backup = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='backup' Line='backup = ""'>
  <DD>Backup prefix for backup images.  If no prefix is specified then no backup
  images are kept when processing.  If specified then the backup image
  has the specified prefix.
  </DD>
  </DL>
  <DL>
  <DT><B>instrument = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='instrument' Line='instrument = ""'>
  <DD>CCD instrument translation file.  This is usually set with
  <B>setinstrument</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>ssfile = "<TT>subsets</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ssfile' Line='ssfile = "subsets"'>
  <DD>Subset translation file used to define the subset identifier.  See
  <B>subsets</B> for more.
  </DD>
  </DL>
  <DL>
  <DT><B>graphics = "<TT>stdgraph</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='graphics' Line='graphics = "stdgraph"'>
  <DD>Interactive graphics output device when fitting the overscan bias vector.
  </DD>
  </DL>
  <DL>
  <DT><B>cursor = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics cursor input.  The default is the standard graphics cursor.
  </DD>
  </DL>
  <DL>
  <DT><B>version = "<TT>June 1987</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='version' Line='version = "June 1987"'>
  <DD>Package version.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The CCD reduction package is loaded when this command is entered.  The
  package contains parameters which affect the operation of the tasks it
  defines.  When images are processed or new image are created the output
  pixel datatype is that specified by the parameter <B>pixeltype</B>.  Note
  that CCD processing replaces the original image by the processed image so
  the pixel type of the CCD images may change during processing.  The output
  pixel type is not allowed to change to a lower precision but it is common
  for input short images to be processed to real images.  Processing images
  from short to real pixel datatypes will generally increase the amount of
  disk space required (a factor of 2 on most computers).
  <P>
  The tasks produce log output which may be printed on the standard
  output (the terminal unless redirected) and appended to a file.  The
  parameter <I>verbose</I> determines whether processing information
  is printed.  This may be desirable initially, but when using background
  jobs the verbose output should be turned off.  The user may look at
  the end of the log file (for example with <B>tail</B>) to determine
  the status of the processing.
  <P>
  The package was designed to work with data from many different observatories
  and instruments.  In order to accomplish this an instrument translation
  file is used to define a mapping between the package parameters and
  the particular image header format.  The instrument translation file
  is specified to the package by the parameter <I>instrument</I>.  This
  parameter is generally set by the task <B>setinstrument</B>.  The other
  file used is a subset file.  This is generally created and maintained
  by the package and the user need not do anything.  For more sophisticated
  users see <B>instruments</B> and <B>subsets</B>.
  <P>
  The package has very little graphics
  output.  The exception is the overscan bias subtraction.  The bias
  vector is logged in the metacode plot file if given.  The plot file
  may be examined with the tasks in the <B>plot</B> package such as
  <B>gkimosaic</B>.  When interactively fitting the overscan vector
  the graphics input and output devices must be specified.  The defaults
  should apply in most cases.
  <P>
  Because processing replaces the input image by the processed image it
  may be desired to save the original image.  This may be done by
  specifying a backup prefix with the parameter <I>backup</I>.  For
  example, if the prefix is "<TT>orig</TT>" and the image is "<TT>ccd001</TT>", the backup
  image will be "<TT>origccd001</TT>".  The prefix may be a directory but it must
  end with <TT>'/'</TT> or <TT>'$'</TT> (for logical directories).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdproc, instruments, setinstrument, subsets
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'SEE ALSO'  >
  
