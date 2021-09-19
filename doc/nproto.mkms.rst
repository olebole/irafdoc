.. _mkms:

mkms: Create multispec from 1D spectra including associated bands
=================================================================

**Package: nproto**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  mkms -- make multispec format from 1D arrays with associated bands
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  mkms output spectra raw background sigma
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>Name of output multispec image.
  </dd>
  </dl>
  <dl>
  <dt><b>spectra</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='spectra' Line='spectra' -->
  <dd>List of primary 1D spectra to be included in multispec image.
  </dd>
  </dl>
  <dl>
  <dt><b>raw</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='raw' Line='raw' -->
  <dd>List of 1D raw or secondary spectra.  If none specify <tt>""</tt> otherwise
  the list must match the list of primary spectra.
  </dd>
  </dl>
  <dl>
  <dt><b>background</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='background' Line='background' -->
  <dd>List of 1D background spectra.  If none specify <tt>""</tt> otherwise
  the list must match the list of primary spectra.
  </dd>
  </dl>
  <dl>
  <dt><b>sigma</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='sigma' Line='sigma' -->
  <dd>List of 1D sigma spectra.  If none specify <tt>""</tt> otherwise
  the list must match the list of primary spectra.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  MKMS creates a multispec format from 1D spectra.  Unlike SCOPY it
  can include associated spectra.  There can be any number of primary 1D
  spectra and the associated spectra are optional.  However, when
  associated spectra are specified the list must match the primary spectra
  list and the arrays must have the same number of pixels and dispersion
  as the primary spectrum.  The different spectra may have different
  dispersions.
  </p>
  <p>
  This is a simple script using SCOPY and IMSTACK.  It has minimal error
  checking.  In particular, if the set of input is not consistent the
  task will abort with an error leaving temporary files behind.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To create an image with one spectrum and each of the associated types:
  </p>
  <pre>
      cl&gt; mkms out.ms spec rawspec bkgspec sigspec
  </pre>
  <p>
  2. To create an image with three primary spectra and error arrays:
  </p>
  <pre>
      cl&gt; mkms out.ms spec1,spec2,spec3 "" "" err1,err2,err3
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>MKMS V2.12.2</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='MKMS' Line='MKMS V2.12.2' -->
  <dd>This prototype task added for this release.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  scopy, imstack
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  -->
  
