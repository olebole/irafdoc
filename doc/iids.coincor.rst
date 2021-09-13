.. _coincor:

coincor — Correct spectra for detector count rates
==================================================

**Package: iids**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  coincor -- Correct detector count rates
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  coincor input records
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
  <DD>This is the root file name for the corrected spectra.  If no root name
  is specified (specified with the null string "<TT></TT>") then the operation
  is done in place.
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
  <DT><B>ccmode = )_.ccmode</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccmode' Line='ccmode = )_.ccmode'>
  <DD>The mode used to model the detector count rate corrections.
  In the following C(obs) is the observed count rate and C(cor) is the
  corrected count rate.
  <DL>
  <DT><B>"<TT>photo</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"photo"'>
  <DD>Photoelectric photometer with discriminator mode.  The count rate
  correction is
  <P>
      C(cor) = C(obs) * exp (C(obs) * deadtime)
      
  where the parameter <I>deadtime</I> is the representative deadtime in seconds.
  </DD>
  </DL>
  <DL>
  <DT><B>"<TT>iids</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"iids"'>
  <DD>IIDS correction given by
  <P>
      C(cor) = (-ln(1-C(obs)*deadtime)/deadtime)**power
  <P>
  where <B>deadtime</B> is a parameter related to the sweep time used to
  correct for coincidence losses and <B>power</B> is a power law coefficient.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>deadtime = )_.deadtime</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='deadtime' Line='deadtime = )_.deadtime'>
  <DD>For the "<TT>photo</TT>" mode this parameter is the period, in seconds, during
  which no counts can be registered by the detector.  Note that this is
  based on a per pixel basis.  So if the discriminator dead period is of
  order 50 nanoseconds and 2000 pixels are observed per readout, the
  effective deadtime is about 10E-4 seconds.  For the "<TT>iids</TT>" mode this
  parameter defines the sweep time correction and has a value of 1.424E-3
  seconds.
  </DD>
  </DL>
  <DL>
  <DT><B>power = )_.power</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='power' Line='power = )_.power'>
  <DD>The IIDS power law coefficient.  The standard value is 0.975.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The input spectra are corrected for detector count rate errors.  If no
  output root name is given then the operation is done in place.  The type
  of correction is specified by the parameter <I>ccmode</I>.  The available
  modes are for a general photomultiplier with discriminator coincidence
  correction, and the NOAO IIDS.  The parameters for these modes are
  <I>deadtime</I> and <I>power</I>.  The exposure time, in seconds, is a
  required image header parameter (keyword = EXPOSURE).
  <P>
  The default mode is for the NOAO IIDS.  The IIDS correction includes a
  power law correction for a nonlinear effect in the IIDS image tube chain
  which is not included by the mountain reduction software at the telescope.
  If the spectra have been coincidence corrected at the telescope
  then only the nonlinear power law correction is applied.
  <P>
  The coincidence correction flag may take the values -1 for no correction,
  0 for the IIDS correction with <I>power</I> = 1 (the correction
  applied by the mountain reduction software), 1 for the full IIDS
  correction, and 2 for the photomuliplier mode correction.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example corrects a series of IIDS spectra:
  <P>
  	cl&gt; coincor nite1 1-250 output=nite1cc start_rec=1
  <P>
  The following example corrects a series of spectra from the
  Lick ITS:
  <P>
  <PRE>
  	cl&gt; coincor its 1-250 output=itscc start=1 ccmode=photo \<BR>
  	&gt;&gt;&gt; deadtime=2.4E-4 power=1
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <B>Coincor</B> requires approximately 1 second per spectrum of length 1024.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  <PRE>
  The <B>imred.iids</B> package is designed for reducing NOAO IIDS spectra.
  </PRE>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'SEE ALSO'  >
  
