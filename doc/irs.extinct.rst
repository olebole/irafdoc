.. _extinct:

extinct — Use BSWITCH for extinction correction
===============================================

**Package: irs**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  extinct -- Correct spectra for atmospheric extinction
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  extinct root records output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>root</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='root' Line='root'>
  <DD>The root name for the input spectra to be corrected.
  </DD>
  </DL>
  <DL>
  <DT><B>records</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The range of spectra to be included in the extinction operation.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The root name for the output corrected spectra
  </DD>
  </DL>
  <DL>
  <DT><B>start_rec</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='start_rec' Line='start_rec'>
  <DD>The starting record number for the output corrected spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>nr_aps = 2</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nr_aps' Line='nr_aps = 2'>
  <DD>The number of instrument apertures for this data set.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The input spectra are corrected for atmospheric extinction. 
  EXTINCT redirects the spectra through the task BSWITCH so all
  procedures are identical to those described for that task.
  <P>
  Because BSWITCH attempts to perform a beam-switch operation
  unless the subset parameter is equal to the number of
  instrument apertures (in which case beam-switching degenerates
  to a copy operation), the hidden parameter nr_aps should be set
  appropriately to the instrument. For IIDS and IRS data, this
  is 2.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  	cl&gt; extinct  nite1 1001-1032 nite1ex
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The input string of spectra must be ordered so that only
  one spectrum from each aperture is present among substrings
  of length nr_aps.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  bswitch
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
