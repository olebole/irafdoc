.. _imscale:

imscale — Scale an image to a specified (windowed) mean
=======================================================

**Package: proto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imscale -- Scale an image to a specified windowed mean
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  imscale input output mean
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input image to be scaled.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output scaled image.
  </DD>
  </DL>
  <DL>
  <DT><B>mean</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mean' Line='mean'>
  <DD>Scale the output image to this mean value.
  </DD>
  </DL>
  <DL>
  <DT><B>lower = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = INDEF'>
  <DD>Lower limit of window for calculating the input image mean.  INDEF corresponds
  to the minimum possible pixel value.
  </DD>
  </DL>
  <DL>
  <DT><B>upper = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = INDEF'>
  <DD>Upper limit of window for calculating the input image mean.  INDEF corresponds
  to the maximum possible pixel value.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print the calculated input and output image means.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The mean of the <I>input</I> image between the limits <I>lower</I>
  and <I>upper</I> is computed.  The image is then scaled to the
  specified output <I>mean</I>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To scale an image to a unit mean excluding deviant points below
  1000 and above 5000.
  <P>
  <PRE>
      cl&gt; imscale calib flat 1 lower=1000 upper=5000
  </PRE>
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
