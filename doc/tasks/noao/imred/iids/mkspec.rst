.. _mkspec:

mkspec: Generate an artificial spectrum
=======================================

**Package: iids**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mkspec image_name image_title ncols nlines function
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>image_name</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image_name' Line='image_name' -->
  <dd>The name to be given to the image file
  </dd>
  </dl>
  <dl>
  <dt><b>image_title</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='image_title' Line='image_title' -->
  <dd>A character string to be used to describe the image
  </dd>
  </dl>
  <dl>
  <dt><b>ncols</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ncols' Line='ncols' -->
  <dd>The number of pixels in the spectrum (the length of the image).
  </dd>
  </dl>
  <dl>
  <dt><b>nlines</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='nlines' Line='nlines' -->
  <dd>The number or lines (rows) in the image.
  </dd>
  </dl>
  <dl>
  <dt><b>function</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='function' Line='function' -->
  <dd>An indicator specifying the form of the spectrum: 1 - a constant,
  2 - a ramp running from start_level to end_level, 3 - a black body
  extending in wavelength (Angstroms) from start_wave to end_wave
  at a given temperature (in degrees K).
  </dd>
  </dl>
  <dl>
  <dt><b>constant</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='constant' Line='constant' -->
  <dd>The value to be assigned to the spectrum if function=1 (constant).
  </dd>
  </dl>
  <dl>
  <dt><b>start_level</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='start_level' Line='start_level' -->
  <dd>The starting value to be assigned to the spectrum at pixel 1 if
  function=2 (ramp).
  </dd>
  </dl>
  <dl>
  <dt><b>end_level</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='end_level' Line='end_level' -->
  <dd>The ending value of the spectrum assigned at pixel=ncols if function=2.
  </dd>
  </dl>
  <dl>
  <dt><b>start_wave</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='start_wave' Line='start_wave' -->
  <dd>The wavelength (Angstroms) assigned to pixel 1 if function=3 (Black Body).
  </dd>
  </dl>
  <dl>
  <dt><b>end_wave</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='end_wave' Line='end_wave' -->
  <dd>The wavelength (Angstroms) assigned to the last pixel if function=3.
  </dd>
  </dl>
  <dl>
  <dt><b>temperature</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='temperature' Line='temperature' -->
  <dd>The black body temperature (degrees K) for which the spectrum
  is to be created if function=3.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  An artificial image is created with the specified name and length.
  The image may have a constant value (function=1), or may be a ramp
  with either positive or negative slope (function=2), or may be
  a black body curve (function=3).
  </p>
  <p>
  Only those parameters specific to the functional form of the image
  need be specified. In all cases the parameters image_name, image_title,
  ncols, nlines, and function are required. If function=1, parameter constant
  is required; if function=2, start_level and end_level are required;
  if function=3, start_wave, end_wave, and temperature are required.
  </p>
  <p>
  All black body functions are normalized to 1.0 at their peak
  intensity which may occur at a wavelength beyond the extent of
  the generated spectrum.
  </p>
  <p>
  NOTE THAT THIS TASK IS OBSOLETE AND ARTDATA.MK1DSPEC SHOULD BE USED.
  In particular this task does not set the header dispersion coordinate
  system.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <pre>
  	cl&gt; mkspec allones "Spectrum of 1.0" 1024 1 1 constant=1.0
  	cl&gt; mkspec ramp "From 100.0 to 0.0" 1024 64 2 start=100 \<br>
  	&gt;&gt;&gt; end=0.0
  	cl&gt; mkspec bb5000 "5000 deg black body" 512 1 3 start=3000 \<br>
  	&gt;&gt;&gt; end=8000 temp=5000
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>MKSPEC V2.10</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='MKSPEC' Line='MKSPEC V2.10' -->
  <dd>This task is unchanged.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  artdata.mk1dspec, artdata.mk2dspec, artdata.mkechelle
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  -->
  
