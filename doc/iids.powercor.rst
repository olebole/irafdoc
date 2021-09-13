.. _powercor:

powercor — Apply power law correction to mountain reduced spectra
=================================================================

**Package: iids**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  powercor -- Apply power law correction to mountain reduced spectra
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  powercor input records
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The root file name of the input spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>records</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The range of spectra.
  The names of the spectra will be formed by appending the range
  elements to the input root name.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>This is the root file name for the corrected spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>start_rec = 1</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='start_rec' Line='start_rec = 1'>
  <DD>The starting record number to be appended to the root name of the
  created spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>power = )iids.power</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='power' Line='power = )iids.power'>
  <DD>The power law coefficient.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A power law correction to the IIDS count rates is applied to the input
  spectra.  The mountain reduction software applies a coincidence correction
  to the observed IIDS count rates but does not correct for a nonlinear effect
  in the image tube chain.  This second correction takes the form of a
  power law
  <P>
  	C(out) = C(in) ** power
  <P>
  where C(in) is the input, coincidence corrected, count rate and C(out)
  is the corrected count rate.  The power is a parameter of the task
  which defaults to the <B>iids</B> package parameter set to the appropriate
  value for the IIDS.  The exposure time, in seconds, is a required
  image header parameter (keyword = EXPOSURE) used to convert the
  total counts to count rates.
  <P>
  Note that if the original raw spectra are being reduced then the either
  <B>coincor</B> or <B>powercor</B> may be used to apply both the coincidence
  correction and the power law correction at the same time.  In other words,
  the tasks apply the coincidence correction if the coincidence flag (CO-FLAG) is
  -1 (uncorrected) and the power law correction alone if the flag is zero
  (coincidence corrected only).  The flag is 1 when both the coincidence and
  nonlinear correction have been applied.
  <P>
  This task is a script calling <B>coincor</B> with <I>ccmode</I> = "<TT>iids</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example corrects a series of IIDS spectra:
  <P>
  	cl&gt; powercor nite1 1-250 output=nite1cc start_rec=1
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  coincor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
