.. _mkms:

mkms — Create multispec from 1D spectra including associated bands
==================================================================

**Package: nproto**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkms -- make multispec format from 1D arrays with associated bands
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkms output spectra raw background sigma
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Name of output multispec image.
  </DD>
  </DL>
  <DL>
  <DT><B>spectra</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='spectra' Line='spectra'>
  <DD>List of primary 1D spectra to be included in multispec image.
  </DD>
  </DL>
  <DL>
  <DT><B>raw</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='raw' Line='raw'>
  <DD>List of 1D raw or secondary spectra.  If none specify "<TT></TT>" otherwise
  the list must match the list of primary spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>background</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='background' Line='background'>
  <DD>List of 1D background spectra.  If none specify "<TT></TT>" otherwise
  the list must match the list of primary spectra.
  </DD>
  </DL>
  <DL>
  <DT><B>sigma</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma'>
  <DD>List of 1D sigma spectra.  If none specify "<TT></TT>" otherwise
  the list must match the list of primary spectra.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  MKMS creates a multispec format from 1D spectra.  Unlike SCOPY it
  can include associated spectra.  There can be any number of primary 1D
  spectra and the associated spectra are optional.  However, when
  associated spectra are specified the list must match the primary spectra
  list and the arrays must have the same number of pixels and dispersion
  as the primary spectrum.  The different spectra may have different
  dispersions.
  <P>
  This is a simple script using SCOPY and IMSTACK.  It has minimal error
  checking.  In particular, if the set of input is not consistent the
  task will abort with an error leaving temporary files behind.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To create an image with one spectrum and each of the associated types:
  <P>
  <PRE>
      cl&gt; mkms out.ms spec rawspec bkgspec sigspec
  </PRE>
  <P>
  2. To create an image with three primary spectra and error arrays:
  <P>
  <PRE>
      cl&gt; mkms out.ms spec1,spec2,spec3 "" "" err1,err2,err3
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>MKMS V2.12.2</B></DT>
  <! Sec='REVISIONS' Level=0 Label='MKMS' Line='MKMS V2.12.2'>
  <DD>This prototype task added for this release.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  scopy, imstack
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
