.. _quadjoin:

quadjoin: Rejoin single amplifier images produced by quadsplit
==============================================================

**Package: quadred**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  quadjoin -- Split quadformat data into single amplifier images
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  quadjoin input
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>Root name of images to be joined.  Extensions based on the AMPLIST
  keyword are applied to the root name.  This task does not
  allow a list of input root names.
  </dd>
  </dl>
  <dl>
  <dt><b>output = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output = ""' -->
  <dd>Output image name.  If one is not given then the input root name is used.
  </dd>
  </dl>
  <dl>
  <dt><b>delete = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='delete' Line='delete = no' -->
  <dd>Delete subimages on completion?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Images in split <span style="font-family: monospace;">"quadformat"</span> (see help topic <b>quadformat</b> and
  <b>quadsplit</b>) are rejoined into <span style="font-family: monospace;">"quadformat"</span>.  The input images
  have a common root name and then an extension given by the amplifier
  labels in the AMPLIST keyword are added.  The output name may be specified
  or the input root name may be used.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To join a split set of images:
  </p>
  <pre>
      qu&gt; dir quad0072*
      quad0072.11.imh     quad0072.21.imh
      quad0072.12.imh     quad0072.22.imh     
      qu&gt; quadjoin quad0072 delete+
      qu&gt; dir quad0072*
      quad0072.imh
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  quadformat, quadsplit
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
