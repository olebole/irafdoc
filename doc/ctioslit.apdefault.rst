.. _apdefault:

apdefault — Set the default aperture parameters
===============================================

**Package: ctioslit**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  apdefault -- Set default aperture parameters for the package
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  apdefault
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>lower = -5., upper = 5.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = -5., upper = 5.'>
  <DD>Default lower and upper aperture limits relative to the aperture center.
  These limits are used for apertures found with <B>apfind</B> and when
  defining the first aperture in <B>apedit</B>.
  </DD>
  </DL>
  <DL>
  <DT><B>apidtable = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apidtable' Line='apidtable = ""'>
  <DD>Aperture identification table.  This may be either a text file or an
  image.  A text file consisting of lines with an aperture number, beam
  number, and aperture title or identification.  An image will contain the
  keywords SLFIBnnn with string value consisting of aperture number, beam
  number, optional right ascension and declination, and aperture title.  This
  information is used to assign aperture information automatically in
  <B>apfind</B> and <B>apedit</B>.
  </DD>
  </DL>
  <P>
  <CENTER>Default Background Subtraction Parameters
  
  </CENTER><BR>
  <DL>
  <DT><B>b_function = "<TT>chebyshev</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_function' Line='b_function = "chebyshev"'>
  <DD>Default background fitting function.  The fitting function types are
  "<TT>chebyshev</TT>" polynomial, "<TT>legendre</TT>" polynomial, "<TT>spline1</TT>" linear spline, and
  "<TT>spline3</TT>" cubic spline.
  </DD>
  </DL>
  <DL>
  <DT><B>b_order = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_order' Line='b_order = 1'>
  <DD>Default background function order.  The order refers to the number of
  terms in the polynomial functions or the number of spline pieces in the spline
  functions.
  </DD>
  </DL>
  <DL>
  <DT><B>b_sample = "<TT>-10:-6,6:10</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_sample' Line='b_sample = "-10:-6,6:10"'>
  <DD>Default background sample.  The sample is given by a set of colon separated
  ranges each separated by either whitespace or commas.  The string "<TT>*</TT>" refers
  to all points.  Note that the background coordinates are relative to the
  aperture center and not image pixel coordinates so the endpoints need not
  be integer.
  </DD>
  </DL>
  <DL>
  <DT><B>b_naverage = -3</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_naverage' Line='b_naverage = -3'>
  <DD>Default number of points to average or median.  Positive numbers
  average that number of sequential points to form a fitting point.
  Negative numbers median that number, in absolute value, of sequential
  points.  A value of 1 does no averaging and each data point is used in the
  fit.
  </DD>
  </DL>
  <DL>
  <DT><B>b_niterate = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_niterate' Line='b_niterate = 0'>
  <DD>Default number of rejection iterations.  If greater than zero the fit is
  used to detect deviant fitting points and reject them before repeating the
  fit.  The number of iterations of this process is given by this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>b_low_reject = 3., b_high_reject = 3.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_low_reject' Line='b_low_reject = 3., b_high_reject = 3.'>
  <DD>Default background lower and upper rejection sigmas.  If greater than zero
  points deviating from the fit below and above the fit by more than this
  number of times the sigma of the residuals are rejected before refitting.
  </DD>
  </DL>
  <DL>
  <DT><B>b_grow = 0.</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='b_grow' Line='b_grow = 0.'>
  <DD>Default reject growing radius.  Points within a distance given by this
  parameter of any rejected point are also rejected.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task sets the values of the default aperture parameters for the
  tasks <B>apedit</B> and <B>apfind</B> which define new apertures.  For a
  description of the components of an aperture see the paper <B>The
  APEXTRACT Package</B>.  In <B>apedit</B> the default aperture limits and
  background parameters are only used if there are no other
  apertures defined.  The aperture identification table is used when
  reordering the apertures with the <TT>'o'</TT> key.  When run the parameters are
  displayed and modified using the <B>eparam</B> task.
  <P>
  The aperture limits and background fitting sample regions are defined
  relative to the center of the aperture.  The background fitting parameters
  are those used by the ICFIT package.  They may be modified interactively
  with the <TT>'b'</TT> key in the task <B>apedit</B>.  For more on background fitting
  and subtracting see <B>apbackground</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To review and modify the default aperture parameters:
  <P>
  	cl&gt; apdefault
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>APDEFAULT V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='APDEFAULT' Line='APDEFAULT V2.11'>
  <DD>The aperture ID table information may now be contained in the
  image header under the keywords SLFIBnnn.
  </DD>
  </DL>
  SEE ALSO
  apbackground, apedit, apfind, icfit
  </UL>
  <! EndSection:    'REVISIONS'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS'  >
  
