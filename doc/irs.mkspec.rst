.. _mkspec:

mkspec — Generate an artificial spectrum
========================================

**Package: irs**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkspec -- generate an artificial spectrum or image (obsolete)
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkspec image_name image_title ncols nlines function
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>image_name</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image_name' Line='image_name'>
  <DD>The name to be given to the image file
  </DD>
  </DL>
  <DL>
  <DT><B>image_title</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='image_title' Line='image_title'>
  <DD>A character string to be used to describe the image
  </DD>
  </DL>
  <DL>
  <DT><B>ncols</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols'>
  <DD>The number of pixels in the spectrum (the length of the image).
  </DD>
  </DL>
  <DL>
  <DT><B>nlines</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines'>
  <DD>The number or lines (rows) in the image.
  </DD>
  </DL>
  <DL>
  <DT><B>function</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function'>
  <DD>An indicator specifying the form of the spectrum: 1 - a constant,
  2 - a ramp running from start_level to end_level, 3 - a black body
  extending in wavelength (Angstroms) from start_wave to end_wave
  at a given temperature (in degrees K).
  </DD>
  </DL>
  <DL>
  <DT><B>constant</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant'>
  <DD>The value to be assigned to the spectrum if function=1 (constant).
  </DD>
  </DL>
  <DL>
  <DT><B>start_level</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='start_level' Line='start_level'>
  <DD>The starting value to be assigned to the spectrum at pixel 1 if
  function=2 (ramp).
  </DD>
  </DL>
  <DL>
  <DT><B>end_level</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='end_level' Line='end_level'>
  <DD>The ending value of the spectrum assigned at pixel=ncols if function=2.
  </DD>
  </DL>
  <DL>
  <DT><B>start_wave</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='start_wave' Line='start_wave'>
  <DD>The wavelength (Angstroms) assigned to pixel 1 if function=3 (Black Body).
  </DD>
  </DL>
  <DL>
  <DT><B>end_wave</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='end_wave' Line='end_wave'>
  <DD>The wavelength (Angstroms) assigned to the last pixel if function=3.
  </DD>
  </DL>
  <DL>
  <DT><B>temperature</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='temperature' Line='temperature'>
  <DD>The black body temperature (degrees K) for which the spectrum
  is to be created if function=3.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  An artificial image is created with the specified name and length.
  The image may have a constant value (function=1), or may be a ramp
  with either positive or negative slope (function=2), or may be
  a black body curve (function=3).
  <P>
  Only those parameters specific to the functional form of the image
  need be specified. In all cases the parameters image_name, image_title,
  ncols, nlines, and function are required. If function=1, parameter constant
  is required; if function=2, start_level and end_level are required;
  if function=3, start_wave, end_wave, and temperature are required.
  <P>
  All black body functions are normalized to 1.0 at their peak
  intensity which may occur at a wavelength beyond the extent of
  the generated spectrum.
  <P>
  NOTE THAT THIS TASK IS OBSOLETE AND ARTDATA.MK1DSPEC SHOULD BE USED.
  In particular this task does not set the header dispersion coordinate
  system.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  	cl&gt; mkspec allones "Spectrum of 1.0" 1024 1 1 constant=1.0
  	cl&gt; mkspec ramp "From 100.0 to 0.0" 1024 64 2 start=100 \<BR>
  	&gt;&gt;&gt; end=0.0
  	cl&gt; mkspec bb5000 "5000 deg black body" 512 1 3 start=3000 \<BR>
  	&gt;&gt;&gt; end=8000 temp=5000
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>MKSPEC V2.10</B></DT>
  <! Sec='REVISIONS' Level=0 Label='MKSPEC' Line='MKSPEC V2.10'>
  <DD>This task is unchanged.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  artdata.mk1dspec, artdata.mk2dspec, artdata.mkechelle
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
