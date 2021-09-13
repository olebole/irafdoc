seepsf — Compute an image from the point spread function
========================================================

**Package: daophot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>seepsf (May00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.digiphot.daophot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>seepsf (May00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>seepsf</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  seepsf -- convert a sampled PSF lookup table to a PSF image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  seepsf psfimage image
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_psfimage">psfimage</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='psfimage' Line='psfimage'>
  <DD>The list of input PSF images computed by the PSF task. Each PSF image consists
  of the parameters of a 2D analytic function stored in the image header and an
  optional sampled lookup table of residuals from that fit stored in the image
  pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_image">image</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>The list of output PSF images consisting of the sum of the analytic function
  and the residuals in the lookup table. There must be one output PSF image for
  each input PSF image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dimension">dimension = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dimension' Line='dimension = INDEF'>
  <DD>The dimensions of the output PSF image. By default <I>image</I> is a 2D image
  with dimensions of N by N where N = 2 * nint (psfrad / scale)  + 1 with the
  same scale as the original image from which <I>psfimage</I> was derived.
  <I>Psfrad</I> is the PSF fitting radius stored in the <I>psfimage</I> image
  header parameter "<TT>PSFRAD</TT>". <I>Scale</I> is the image scale stored in the image
  header parameter "<TT>SCALE</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xpsf">xpsf = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='xpsf' Line='xpsf = INDEF'>
  <DD>The x coordinate of the output PSF. <I>Xpsf</I> is only used if <I>psfimage</I>
  was computed with the variable PSF parameter <I>varorder</I> in the DAOPARS task
  set to &gt; 0.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ypsf">ypsf = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ypsf' Line='ypsf = INDEF'>
  <DD>The y coordinate of the output PSF. <I>Ypsf</I> is only used if <I>psfimage</I>
  was computed with the variable PSF parameter <I>varorder</I> in the DAOPARS task
  set to &gt; 0.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_magnitude">magnitude = INDEF</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='magnitude' Line='magnitude = INDEF'>
  <DD>The intensity scale of the output PSF. By default the intensity scale is set by
  the magnitude of the first star used by the PSF task to compute <I>psfimage</I>.
  This parameter is stored in the keyword "<TT>PSFMAG</TT>" in <I>psfimage</I>.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  SEEPSF takes the input PSF <I>psfimage</I> computed by the PSF task, consisting
  of the parameters of a 2D analytic function stored in the image header and an
  optional lookup table of residuals from the fit stored in the image pixels, and
  computes an output PSF, <I>image</I>, consisting of the sum of the analytic
  function and the residuals.
  <P>
  By default <I>image</I> is a 2D image of dimensions N by N where N = 2 * nint
  (psfrad) + 1 and the scale of <I>image</I> is the same as the scale of the
  original image from which <I>psfimage</I>  was derived. If <I>dimension</I> is
  greater or less than N then the output PSF is block-averaged or subsampled with
  respect to the original image. <I>Psfrad</I> is the value of the psf radius
  parameter in the task DAOPARS used to compute <I>psfimage</I> and is stored in
  the <I>psfimage</I> header parameter "<TT>PSFRAD</TT>".
  <P>
  If <I>psfimage</I> was computed with the variable PSF parameter <I>varorder</I>
  set to &gt; 0, then <I>image</I> is computed at a point (xpsf, ypsf) defined
  relative to the original image.  By default <I>image</I> is computed at the
  centroid of the PSF defined by the <I>psfimage</I> header parameters "<TT>XPSF</TT>"
  and "<TT>YPSF</TT>".
  <P>
  The intensity scale of <I>image</I> is determined by the value of <I>magnitude</I>
  relative to the magnitude of the PSF. By default the output PSF has the
  magnitude of the first PSF star stored in the <I>psfimage</I> header parameter
  "<TT>PSFMAG</TT>".
  <P>
  SEEPSF is most commonly used for visualizing the PSF in image scale coordinates
  and checking the form of any variability as a function of position. However
  <I>image</I> can also be used as input to other image processing program, for
  example it might be used as the kernel in a convolution operation.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Compute the output PSF in image scale coordinates of PSF function
  for image dev$ypix.
  <P>
  <PRE>
      da&gt; seepsf ypix.psf.3 ypixpsf
  </PRE>
  <P>
  2. Compute the output PSF in image scale coordinates of the variable
  PSF for the image m92b at position (113.63,50.48) pixels relative to the
  original image.
  <P>
  <PRE>
      da&gt; seepsf m92b.psf.2 m92psf xpsf=113.63 ypsf=50.48
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  datapars,daopars,psf
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>