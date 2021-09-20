.. _slist:

slist: List spectrum header parameters
======================================

**Package: specred**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  slist1d input records
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The image root name for the spectra to be listed.
  </dd>
  </dl>
  <dl>
  <dt><b>records</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='records' Line='records' -->
  <dd>The record string for the spectra to be listed. The records will be appended
  to the root name to form image names of the type <span style="font-family: monospace;">"root.xxxx"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>long_header = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='long_header' Line='long_header = no' -->
  <dd>If set to yes, then a complete listing of the header elements
  is given. If set to no, then a single line per spectrum is given which lists
  in the following order: the image name, object or sky spectrum, exposure
  time, spectrum length, and image title.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Each spectrum in the list implied by the root name and the record string
  is opened and the header is read. The pixel file is not accessed in order
  to save time. The header listing is directed to STDOUT and may be
  redirected for printing.
  </p>
  <p>
  A warning message is issued if
  a requested image is not found, but otherwise proceeds.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  The following example lists 8 spectral headers in long form on the printer:
  </p>
  <pre>
  	cl&gt; slist1d nite1 1001-1008 | lprint
  </pre>
  <p>
  The next example lists the same spectral headers but in short form
  on the terminal
  </p>
  <pre>
  	cl&gt; slist1d nite1 1001-1008 long-
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>SLIST1D V2.10</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='SLIST1D' Line='SLIST1D V2.10' -->
  <dd>This task is the same as V2.9 <b>slist</b> and applies only to the older
  IRS/IIDS record extension spectra.  In V2.10 <b>slist</b>
  has been revised for multiaperture spectra.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  SLIST1D does not inform the user if the pixel file can or cannot be read.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  slist, imheader
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'BUGS' 'SEE ALSO'  -->
  
