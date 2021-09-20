.. _chpixtype:

chpixtype: Change the pixel type of a list of images
====================================================

**Package: imutil**

.. raw:: html

  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  chpixtype input output newpixtype
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>The list of input images.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>The list of output images. If the output image list is the same as the input
  image list then the original images are overwritten.
  </dd>
  </dl>
  <dl>
  <dt><b>newpixtype</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='newpixtype' Line='newpixtype' -->
  <dd>The pixel type of the output image. The options are: <span style="font-family: monospace;">"ushort"</span>, <span style="font-family: monospace;">"short"</span>,
  <span style="font-family: monospace;">"int"</span>, <span style="font-family: monospace;">"long"</span>, <span style="font-family: monospace;">"real"</span>, <span style="font-family: monospace;">"double"</span> and <span style="font-family: monospace;">"complex"</span>.
  </dd>
  </dl>
  <dl>
  <dt><b>oldpixtype = <span style="font-family: monospace;">"all"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='oldpixtype' Line='oldpixtype = "all"' -->
  <dd>The pixel type of the input images to be converted. By default all the
  images in the input list are converted to the pixel type specified by
  newpixtype. The remaining options are <span style="font-family: monospace;">"ushort"</span>, <span style="font-family: monospace;">"short"</span>, <span style="font-family: monospace;">"int"</span>, <span style="font-family: monospace;">"long"</span>,
  <span style="font-family: monospace;">"real"</span>, <span style="font-family: monospace;">"double"</span> and <span style="font-family: monospace;">"complex"</span> in which case only those images of the
  specified type are converted.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes' -->
  <dd>Print messages about actions performed.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The list of images specified by <i>input</i> and pixel type <i>oldpixtype</i> 
  are converted to the pixel type specified by <i>newpixtype</i> and written
  to the list of output images specified by <i>output</i>.
  </p>
  <p>
  Conversion from one pixel type to another is direct and may involve both
  loss of precision and dynamic range. Mapping of floating point numbers
  to integer numbers is done by truncation. Mapping of complex numbers
  to floating point or integer numbers will preserve the real part of the
  complex number only.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Convert a list of images to type real, overwriting the existing images.
  </p>
  <p>
          im&gt; chpixtype nite1*.imh nite1*.imh real
  </p>
  <p>
  2. Convert only those images in imlist1 which are of type short to type real.
     Imlist1 and imlist2 are text files containing the list of input and
     output images respectively. The image names are listed 1 per line.
  </p>
  <p>
          im&gt; chpixtype @imlist1 @imlist2 real old=short
  </p>
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
  imarith
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
