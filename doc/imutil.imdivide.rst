.. _imdivide:

imdivide — Image division with zero checking and rescaling
==========================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imdivide -- image division with zero checking and rescaling
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  imdivide numerator denominator resultant
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>numerator</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='numerator' Line='numerator'>
  <DD>Numerator image.
  </DD>
  </DL>
  <DL>
  <DT><B>denominator</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='denominator' Line='denominator'>
  <DD>Denominator image.
  </DD>
  </DL>
  <DL>
  <DT><B>resultant</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='resultant' Line='resultant'>
  <DD>Resultant image.  This image will be of datatype real.
  </DD>
  </DL>
  <DL>
  <DT><B>title = <TT>'*'</TT></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = '*''>
  <DD>Title for resultant image.  The special character <TT>'*'</TT> defaults the title
  to that of the numerator image.
  </DD>
  </DL>
  <DL>
  <DT><B>constant = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0'>
  <DD>The constant value for the zero division constant option.
  </DD>
  </DL>
  <DL>
  <DT><B>rescale = norescale</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rescale' Line='rescale = norescale'>
  <DD>After the image division the resultant image may be rescaled with the following
  options:
  <DL>
  <DT><B>norescale</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='norescale' Line='norescale'>
  <DD>Do not rescale the resultant image.
  </DD>
  </DL>
  <DL>
  <DT><B>mean</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='mean' Line='mean'>
  <DD>Scale the resultant image to the specified mean value.
  </DD>
  </DL>
  <DL>
  <DT><B>numerator</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='numerator' Line='numerator'>
  <DD>Scale the resultant image to have the same mean value as the numerator image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>mean = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mean' Line='mean = 1'>
  <DD>The mean value used rescale the resultant image under 'mean' option of
  <I>rescale</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print the means of each image?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>numerator</I> image is divided by the <I>denominator</I> image to
  form the <I>resultant</I> image.  The division is checked for division by
  zero and replaces the result with the value of the parameter <I>constant</I>.
  After the division the resultant image may be rescaled.
  The rescaling option is selected with <I>rescale</I>.  The options are
  not to rescale, rescale to the specified <I>mean</I> value, and rescale to
  the mean of the numerator.  The means of the three images are calculated
  and may be printed with the verbose option.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To divide a object image by a flat field and then rescale the division
  back to the mean of the object image:
  <P>
      cl&gt; imdivide object image final rescale=numerator
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imarith
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
