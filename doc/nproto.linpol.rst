linpol — Calculate polarization frames and Stoke's parameters
=============================================================

**Package: nproto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>linpol (Apr92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.nproto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>linpol (Apr92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>linpol</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  linpol -- Calculate linear polarization, angle, and Stokes images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  linpol input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>A list of input images.  There must be either three or four input
  images taken with the polarizer at even multiples of a 45 degree
  position angle.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The output data cube which will contain as separate bands the
  fractional linear polarization and angle frames, and optionally the
  Stokes parameter frames.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_degrees">degrees = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='degrees' Line='degrees = yes'>
  <DD>Report the polarization angle in degrees?  If <B>degrees</B> = no, the
  polarization angle will be reported in radians.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_stokes">stokes = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='stokes' Line='stokes = yes'>
  <DD>Output the Stokes parameter images?  If <B>stokes</B> = yes, the three
  linear Stokes parameters, I, Q, and U, will be included in the
  <B>output</B> data cube as separate bands.  If <B>stokes</B> = no, only
  the fractional linear polarization and angle frames will appear in the
  output.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_normalize">normalize = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='normalize' Line='normalize = no'>
  <DD>Normalize the Q and U frames?  This is appropriate when using a tool
  such as VELVECT to plot the polarization vectors.  If <B>normalize</B> =
  yes, the Q and U Stokes parameter frames will be normalized by dividing
  by the I parameter frame.  This parameter has no effect on either the
  fractional polarization or angle frames.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_keyword">keyword = "<TT>polangle</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='keyword' Line='keyword = "polangle"'>
  <DD>This must be set to the name of a header keyword that contains the
  polarizer angle for each of the <B>input</B> images.  LINPOL will only
  accept polarizer angles at even 45 degree separations.  Either four such
  frames, at 0-45-90-135 degrees, or three frames with any one of the
  0-45-90-135 degree frames omitted, may be specified.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  LINPOL calculates the pixel-by-pixel fractional linear polarization and
  polarization angle for a set of either three or four images taken with
  polarizer set at even multiples of a 45 degree position angle.  At least
  three different frames with the header <B>keyword</B> set to one of
  0, 45, 90, or 135 degrees must be specified in the <B>input</B> list.
  <P>
  If <B>degrees</B> = yes, the output polarization angle band of the image
  will be in units of degrees, if <B>degrees</B> = no, the angle will be
  reported as radians.  If <B>stokes</B> = yes, the output image
  will consist of five separate bands, one each for the pixel-by-pixel
  fractional linear polarization and the corresponding polarization angle,
  and one for each of the I, Q, and U pixel-by-pixel Stokes parameters.
  If <B>stokes</B> = no, only the fractional polarization and the polarization
  angle will be saved in the output.
  <P>
  The <B>normalize</B> parameter is useful for plotting purposes.
  If <B>normalize</B> = yes, the Q and U Stokes parameter frames will be
  normalized by dividing by the I parameter frame.  This may be appropriate
  when using a tool such as VELVECT to plot the polarization vectors.
  This parameter has no effect on either the fractional polarization or
  angle frames.
  <P>
  Each input image must contain the corresponding polarizer angle
  in the header keyword specified by the parameter <B>keyword</B>
  Linpol will only accept polarizer angles at even 45 degree separations.
  Either four such frames, at 0-45-90-135 degrees, or three frames with
  any one of the 0-45-90-135 degree frames omitted, may be specified.
  <P>
  The output image header will include information describing the particular
  input images that went into its generation and the particular nature of
  each band of the output.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  An observer obtained four exposures of a particular field through a
  polarizer set at a position angle of 0-45-90-135 degrees.  The first
  step in producing a good map of the polarized light from (extended
  or point-like) sources in the field is always to register these frames
  very precisely.  A slight mismatch in the positioning of each pixel
  relative to the shoulders of nearby sources or extended emission will
  result in large errors in the determination of the polarization quantities.
  <P>
  Another preprocessing step that may be desirable is to match the PSFs
  (Point Spread Functions) of the various frames.  Ideally, these are
  stable in the raw data (i.e., the seeing at the telescope was constant),
  but if not they must be matched to avoid the same errors as above.  Note
  that it may also be a good idea to "<TT>smooth</TT>" the raw images before
  applying linpol to increase the signal-to-noise of the output.
  <P>
  After guaranteeing the integrity of the input images, the image header
  <B>keyword</B> must be created to contain the position angle.  The hedit
  task can be used to do this:
  <P>
  <PRE>
      hedit im.00 polangle 0 add+
      hedit im.45 polangle 45 add+
      hedit im.90 polangle 90 add+
      hedit im.135 polangle 135 add+
  </PRE>
  <P>
  At this point, the input images are ready to be processed by linpol.
  <P>
  To generate an output image containing the fractional linear
  polarization and polarization angle in separate bands, along with the
  pixel-by-pixel Stokes parameter frames:
  <P>
  <PRE>
      np&gt; linpol im.*.imh polar
  </PRE>
  <P>
  To omit the Stokes parameter frames:
  <P>
  <PRE>
      np&gt; linpol im.*.imh polar stokes-
  </PRE>
  <P>
  To represent the pixel-by-pixel polarization angle in radians, rather
  than degrees:
  <P>
  <PRE>
      np&gt; linpol im.*.imh polar degrees-
  </PRE>
  <P>
  To normalize the Q and U Stokes frames and plot the result with velvect:
  <P>
  <PRE>
      np&gt; linpol im.*.imh polar normalize+
      np&gt; imhead polar lo+
      polar[100,100,5][short]: Linear polarization image
  	No bad pixels, no histogram, min=unknown, max=unknown
  	Line storage mode, physdim [100,100,5], length of user area 2147 s.u.
  	Created Wed 10:15:05 29-Apr-92, Last modified Wed 10:15:05 29-Apr-92
  	Pixel file 'ursa!/ursa/scr3/iraf/seaman/polar.pix' [ok]
  	...
  <P>
  	POL0    = 'im.00.imh'
  	POL45   = 'im.45.imh'
  	POL90   = 'im.90.imh'
  	POL135  = 'im.135.imh'
  	POLAR   = 'Band 1 is the percent polarization'
  	ANGLE   = 'Band 2 is the polarization angle'
  	I-STOKES= 'Band 3 is the Stokes I parameter'
  	Q-STOKES= 'Band 4 is the normalized Stokes Q parameter'
  	U-STOKES= 'Band 5 is the normalized Stokes U parameter'
      np&gt; velvect polar[*,*,4] polar[*,*,5]
  </PRE>
  <P>
  Note that the current version of the velvect task is not particularly
  appropriate for this use.  It has no support for reducing the pixel
  resolution of the output plot:  each pixel will generate a plotted vector
  so that to produce an uncrowded (and low "<TT>noise</TT>") plot, the input images
  or output bands must be manually block averaged or otherwise smoothed.
  In addition, the plotted vectors are directed (little arrows) not
  undirected line segments, and the length of the vectors are not easily
  adjusted.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  velvect, imalign, hedit
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>