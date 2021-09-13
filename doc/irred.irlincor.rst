.. _irlincor:

irlincor — Correct IR imager frames for non-linearity
=====================================================

**Package: irred**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  irlincor -- Correct IR imager frames for non-linearity.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  irlincor input output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of images to be corrected for non-linearity
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The list of corrected output images
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>coeff1 = 1.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coeff1' Line='coeff1 = 1.0'>
  <DD>The first coefficient of the correction function
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>coeff2 = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coeff2' Line='coeff2 = 0.0'>
  <DD>The second coefficient of the correction function
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>coeff3 = 0.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coeff3' Line='coeff3 = 0.0'>
  <DD>The third coefficient of the correction function
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The IR imager frames specified by <I>input</I>, which may be a general image
  template including wild cards or an @list, are corrected for non-linearity
  on a pixel by pixel basis and written to <I>output</I>. The number of output
  images must match the number input. The pixel type of the output image(s) will
  match that of the input image(s), however, internally all calculations are 
  performed as type real. The correction is performed assuming 
  that the non-linearity can be represented by the following simple relationship:
  <PRE>
  <P>
  ADU' = ADU * [ coeff1 + coeff2 * (ADU / 32767) + coeff3 * (ADU / 32767)**2 ]
  <P>
  </PRE>
  The coefficients which occur in this expression are specified by the
  parameters <I>coeff1</I>, <I>coeff2</I> and <I>coeff3</I>. Their values are 
  derived from periodic instrumental calibrations and are believed to be
  fairly constant. The  default values specify a <B>null</B> correction.
  You should consult <B>Jay Elias</B> for the latest values.
  Note that the coefficients are expressed in terms of ADU normalised to the
  maximum possible value 32767, in order that their values can be input
  more easily.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Correct input to output using the default values for the coefficients (not a very rewarding operation!)
  <P>
  <PRE>
  	cl&gt; irlincor input output
  <P>
  </PRE>
  <P>
  2. Correct a list of images in place using specified values for the coefficients
  <P>
  <PRE>
  	cl&gt; irlincor @list @list coeff1=1.0 coeff2=0.1 coeff3=0.01
  <P>
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Authors</H3>
  <! BeginSection: 'AUTHORS'>
  <UL>
  The IRLINCOR task was originally written by Steve Heathcote as part of the
  CTIO package. 
  </UL>
  <! EndSection:   'AUTHORS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The form of the correction equation is currently experimental;
  a higher order polynomial or a different functional form could be accommodated
  very easily if required.
  It may be advisable to carry out the calculations in double precision.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  onedspec.coincor, proto.imfunction
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'AUTHORS' 'BUGS' 'SEE ALSO'  >
  
