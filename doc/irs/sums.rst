.. _sums:

sums: Generate sums of object and sky spectra by aperture
=========================================================

**Package: irs**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  sums input records
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The root file name for the input spectra in the string.
  </dd>
  </dl>
  <dl>
  <dt><b>records</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='records' Line='records' -->
  <dd>The range of spectra indicating the elements of the string.
  The names of the spectra will be formed by appending the range
  elements to the input root name.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>This is the root file name for the names of the spectra which will
  be created by the summation operation.
  </dd>
  </dl>
  <dl>
  <dt><b>start_rec</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='start_rec' Line='start_rec' -->
  <dd>The starting record number to be appended to the root name of the
  created spectra.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  All the object spectra for each aperture are summed, and the
  sky spectra are also summed to produce two new spectra for
  each observing aperture. Exposure times are accumulated.
  No tests are made to check whether the object is consistent
  among the specified spectra. This could be accomplished by
  checking the titles or telescope positions, but it isn't.
  </p>
  <p>
  The header parameters OFLAG and BEAM-NUM must be properly
  set in the headers.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  The following example forms 4 new spectra from nite1.2001-nite1.2002,
  nite1.2003-nite1.2004, ... assuming this string is derived from
  IIDS spectra.
  </p>
  <p>
  	cl&gt; sums nite1 2001-2100
  </p>
  
  <!-- EndSection:    'EXAMPLES' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  -->
  
