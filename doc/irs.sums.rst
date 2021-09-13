.. _sums:

sums — Generate sums of object and sky spectra by aperture
==========================================================

**Package: irs**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  sums -- Generate sums of the sky and object spectra for each aperture
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  sums input records
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The root file name for the input spectra in the string.
  </DD>
  </DL>
  <DL>
  <DT><B>records</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The range of spectra indicating the elements of the string.
  The names of the spectra will be formed by appending the range
  elements to the input root name.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>This is the root file name for the names of the spectra which will
  be created by the summation operation.
  </DD>
  </DL>
  <DL>
  <DT><B>start_rec</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='start_rec' Line='start_rec'>
  <DD>The starting record number to be appended to the root name of the
  created spectra.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  All the object spectra for each aperture are summed, and the
  sky spectra are also summed to produce two new spectra for
  each observing aperture. Exposure times are accumulated.
  No tests are made to check whether the object is consistent
  among the specified spectra. This could be accomplished by
  checking the titles or telescope positions, but it isn't.
  <P>
  The header parameters OFLAG and BEAM-NUM must be properly
  set in the headers.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example forms 4 new spectra from nite1.2001-nite1.2002,
  nite1.2003-nite1.2004, ... assuming this string is derived from
  IIDS spectra.
  <P>
  	cl&gt; sums nite1 2001-2100
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
