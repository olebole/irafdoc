.. _normflat:

normflat — Create a flat field by normalizing and replacing low values
======================================================================

**Package: generic**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  normflat -- Create a flat field by normalizing a calibration image
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  normflat image flatfield
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image' Line='image'>
  <DD>Calibration image to be used.
  </DD>
  </DL>
  <DL>
  <DT><B>flatfield</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flatfield' Line='flatfield'>
  <DD>Flat field to be created.
  </DD>
  </DL>
  <DL>
  <DT><B>norm = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='norm' Line='norm = INDEF'>
  <DD>Normalization factor to be used if not INDEF.  If INDEF the normalization
  factor is automatically determined.
  </DD>
  </DL>
  <DL>
  <DT><B>minflat = INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='minflat' Line='minflat = INDEF'>
  <DD>Minimum data value to be used in determining the normalization and in
  creating the flat field.  Values less than or equal to this value are
  replaced with a flat field value of 1.
  </DD>
  </DL>
  <DL>
  <DT><B>sample_section = "<TT>[]</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sample_section' Line='sample_section = "[]"'>
  <DD>Section of the image to be sampled in determining the normalization if
  norm = INDEF.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A flat field is created from a calibration image by normalizing the calibration
  image.  The normalization is specified with the parameter <I>norm</I>.  If the
  value of <I>norm</I> is INDEF then the normalization is determined by sampling
  the pixels in the sample section with values greater than <I>minflat</I>.
  This task differs from the task <B>normalize</B> in that data values less
  than or equal to <I>minflat</I> are replaced with unity in the normalized
  flat field.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To create a flat field from a calibration image "<TT>quartz</TT>" using pixels
  above 1000 and selecting the normalization to be 3500:
  <P>
  	cl&gt; normflat quartz flat norm=3500 minflat=1000
  <P>
  To determine a normalization from the pixels above 1000 and sampling
  every fifth pixel in each dimension:
  <P>
  <PRE>
  	cl&gt; normflat quartz flat minflat=1000 sample=[*:5,*:5]
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  normalize
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
