.. _hdtoi:

hdtoi — Apply DTOI transformation to density image
==================================================

**Package: dtoi**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  hdtoi -- transform images according to hd curve
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  hdtoi input output database
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images to be transformed.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output image names.
  </DD>
  </DL>
  <DL>
  <DT><B>database</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>Name of text database describing HD curve.
  </DD>
  </DL>
  <DL>
  <DT><B>fog = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fog' Line='fog = ""'>
  <DD>Value of fog level, read from database if unspecified.
  </DD>
  </DL>
  <DL>
  <DT><B>option = "<TT>mean</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='option' Line='option = "mean"'>
  <DD>Option for calculating fog density when <B>fog</B> is a file list, can be
  either "<TT>mean</TT>" or "<TT>median</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>sigma = 3.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma = 3.0'>
  <DD>If <B>fog</B> is a file name, and <B>option</B> = "<TT>mean</TT>", the mean fog density
  is iteratively calculated using this rejection criteria.
  </DD>
  </DL>
  <DL>
  <DT><B>floor = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='floor' Line='floor = 0.0'>
  <DD>Value assigned to levels below fog, can be either 0.0 or -1.0.  
  </DD>
  </DL>
  <DL>
  <DT><B>ceiling = 30000.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ceiling' Line='ceiling = 30000.'>
  <DD>The final intensities are scaled to this value, such that a saturated
  input density equals <B>ceiling</B> on output.
  </DD>
  </DL>
  <DL>
  <DT><B>datatype = "<TT>r</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='datatype' Line='datatype = "r"'>
  <DD>Datatype of output image pixels.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print log of processing to STDOUT.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>hdtoi</I> transforms one image to another as described by the 
  <B>database</B>.  There is only one HD curve per run; the same 
  transformation is applied to all input images.
  <P>
  The fog value can be obtained in three ways: read from the database, read
  as a floating point number, or calculated from a list of fog images.  If 
  parameter <B>fog</B> is not specified, the fog value is read from 
  <B>database</B>.  If <B>fog</B> is specified, it can be entered
  as either a floating point number or as a list of file names.  If the
  value cannot be read as a number, it is assumed to be a file name.  In that
  case, the density of each file in the fog list is calculated and the 
  average of these values is subtracted from <B>input</B> before processing.
  The algorithm used to calculate the fog density is selected by the
  <B>option</B> parameter, and is either a "<TT>mean</TT>" or "<TT>median</TT>" calculation.
  The fog density can be the mean value after pixels more than the specified
  number of sigma have been rejected, or the median value of all the fog spot
  pixels.
  <P>
  The fog value is subtracted from the input image before the transformation
  takes place.  It is possible that some density values will fall below
  the fog level; these values are handled in one of two ways.  Values
  below the fog value are set equal to 0.0 when <B>floor</B> = 0.0.  If 
  <B>floor</B> = -1.0, the resulting intensity = -1 * intensity (abs (value)).
  <P>
  A scaling factor is applied to the final intensities, as typically
  they will be &lt; 1.0.  The <B>ceiling</B> parameter is used to specify what
  value a saturated density is transformed to; all intensities are scaled
  to this upper limit.  The precision of the transformation is unaffected by 
  this parameter, although caution must be used if the output image pixel
  type is an integer.  The user is responsible for choosing
  a <B>ceiling</B> that avoids the truncation of significant digits.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Convert three density images to intensity images as described in database db1.
  <P>
  	cl&gt; hdtoi denin* intim1,intim2,intim3 db1
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  Task <B>hdtoi</B> requires 20 cpu seconds to transform a 512 square image, with
  a 12 bit data range, on a VAX 750
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  spotlist, dematch, hdfit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'SEE ALSO'  >
  
