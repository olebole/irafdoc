.. _subsets:

subsets — Subtract pairs in strings of spectra
==============================================

**Package: irs**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  subsets - Subtract pairs of spectra in a string
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  subsets input records
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
  be created by the subtraction operation.
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
  Pairs of spectra are formed from the input string in the order that
  the record numbers would suggest. 
  The first spectrum in the pair is assumed to be the
  principle spectrum and the second spectrum in the pair is subtracted
  from the first. The result is written out as a new spectrum.
  <P>
  No compensation is made for exposure time during the subtraction.
  The header from the principle spectrum is assigned to the output
  spectrum.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example forms 50 new spectra from nite1.2001-nite1.2002,
  nite1.2003-nite1.2004, ...
  <P>
  	cl&gt; subsets nite1 2001-2100
  <P>
  The following example creates new spectra from the pairs nite2.2001-nite2.2002,
  nite2.2003-nite2.2004 in spite of the order of the record numbers entered.
  <P>
  	cl&gt; subsets nite2 2001,2003,2002,2004
  </UL>
  <! EndSection:    'EXAMPLES'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  >
  
