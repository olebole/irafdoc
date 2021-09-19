.. _flatten:

flatten: Flatten images using a flat field
==========================================

**Package: generic**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  flatten -- Flatten images by dividing by a flat field
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  flatten images flatfield
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>Images to be flattened.
  </dd>
  </dl>
  <dl>
  <dt><b>flatfield</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='flatfield' Line='flatfield' -->
  <dd>Flat field image to be divided into the images.
  </dd>
  </dl>
  <dl>
  <dt><b>minflat = INDEF</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='minflat' Line='minflat = INDEF' -->
  <dd>All flat field pixels less than or equal to this value are replaced by
  unit response.  If INDEF all the flat field pixels are used.
  </dd>
  </dl>
  <dl>
  <dt><b>pixtype = <tt>"real"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = "real"' -->
  <dd>The pixel datatype of the flattened image.  The null string (<tt>""</tt>) defaults
  the pixel datatype to that of the original image before flattening.
  The other choices are <tt>"short"</tt>, <tt>"integer"</tt>, <tt>"long"</tt>, and <tt>"real"</tt>.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  Each of the <i>images</i> is flatten by dividing by the <i>flatfield</i>
  flat field image.  The flattened images replace the original images.
  The pixel datatype of the flattened images is specified by the
  <i>pixtype</i>.  The null string (<tt>""</tt>) leaves the datatype of the images
  unchanged.  Low values in the flat field may be replaced by unit response
  by specifying a <i>minflat</i> value.  All pixels in the flat field less
  than or equal to <i>minflat</i> are given unit response.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  To flatten a set of two dimensional images excluding pixels below
  </p>
  <pre>
  	cl&gt; flatten frame* flat minflat=0.2
  </pre>
  
  <!-- EndSection:    'EXAMPLES' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES'  -->
  
