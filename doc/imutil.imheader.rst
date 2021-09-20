.. _imheader:

imheader: Print an image header
===============================

**Package: imutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  imheader -- list header parameters for a list of images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  imheader [images]
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>List of IRAF images.
  </dd>
  </dl>
  <dl>
  <dt><b>imlist = <span style="font-family: monospace;">"*.imh,*.fits,*.pl,*.qp,*.hhh"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='imlist' Line='imlist = "*.imh,*.fits,*.pl,*.qp,*.hhh"' -->
  <dd>The default IRAF image name template.
  </dd>
  </dl>
  <dl>
  <dt><b>longheader = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='longheader' Line='longheader = no' -->
  <dd>Print verbose image header.
  </dd>
  </dl>
  <dl>
  <dt><b>userfields = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='userfields' Line='userfields = yes' -->
  <dd>If longheader is set print the information in the user area.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  IMHEADER prints header information in various formats for the list of IRAF
  images specified by <i>images</i>, or by the default image name template
  <i>imlist</i>. If <i>longheader</i> = no, the image name,
  dimensions, pixel type and title are printed. If <i>longheader</i> = yes,
  information on the create and modify dates, image statistics and so forth
  are printed. Non-standard IRAF header information can be printed by
  setting <i>userfields</i> = yes.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Print the header contents of a list of IRAF fits images.
  </p>
  <pre>
  	cl&gt; imheader *.fits
  </pre>
  <p>
  2. Print the header contents of a list of old IRAF format images in verbose
  mode.
  </p>
  <pre>
  	cl&gt; imheader *.imh lo+
  </pre>
  <p>
  3. Print short headers for all IRAF images of all types, e.g. imh, fits etc
  in the current directory.
  </p>
  <pre>
  	cl&gt; imheader
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imgets, hedit, hselect
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
