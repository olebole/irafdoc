.. _imsum:

imsum: Compute the sum, average, or median of a set of images
=============================================================

**Package: imutil**

.. raw:: html

  <h3>Usage	</h3>
  <!-- BeginSection: 'USAGE	' -->
  <p>
  imsum input output
  </p>
  <!-- EndSection:   'USAGE	' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>input</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='input' Line='input' -->
  <dd>Input images.
  </dd>
  </dl>
  <dl>
  <dt><b>output</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='output' Line='output' -->
  <dd>Output image.
  </dd>
  </dl>
  <dl>
  <dt><b>title = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='title' Line='title = ""' -->
  <dd>Image title for the output image.  If null (<span style="font-family: monospace;">""</span>) then the title of the
  first image is used.
  </dd>
  </dl>
  <dl>
  <dt><b>hparams = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='hparams' Line='hparams = ""' -->
  <dd>List of image header parameters to be summed or averaged.  This feature
  is only used when summing or averaging and no correction is made for
  rejected pixels.  It is primarily used to sum exposure times.
  </dd>
  </dl>
  <dl>
  <dt><b>pixtype = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = ""' -->
  <dd>Pixel datatype for the output image.  The pixel datatypes are <span style="font-family: monospace;">"double"</span>,
  <span style="font-family: monospace;">"real"</span>, <span style="font-family: monospace;">"long"</span>, <span style="font-family: monospace;">"integer"</span>, <span style="font-family: monospace;">"ushort"</span>, and <span style="font-family: monospace;">"short"</span> in order of precedence.
  If null (<span style="font-family: monospace;">""</span>) then the calculation type is used.
  The datatypes may be abbreviated to a single character.
  </dd>
  </dl>
  <dl>
  <dt><b>calctype = <span style="font-family: monospace;">""</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='calctype' Line='calctype = ""' -->
  <dd>Calculation type.  The calculation types are <span style="font-family: monospace;">"double"</span>, <span style="font-family: monospace;">"real"</span>, <span style="font-family: monospace;">"long"</span>,
  <span style="font-family: monospace;">"integer"</span>, and <span style="font-family: monospace;">"short"</span> in order of precedence.  If null (<span style="font-family: monospace;">""</span>) then the
  highest precedence datatype of the input images is used.
  If there is a mixture of <span style="font-family: monospace;">"short"</span> and <span style="font-family: monospace;">"ushort"</span> images then the highest
  precedence datatype will be <span style="font-family: monospace;">"int"</span>.
  The calculation types may be abbreviated to a single character.
  </dd>
  </dl>
  <dl>
  <dt><b>option = <span style="font-family: monospace;">"sum"</span></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='option' Line='option = "sum"' -->
  <dd>Output options are <span style="font-family: monospace;">"sum"</span>, <span style="font-family: monospace;">"average"</span>, or <span style="font-family: monospace;">"median"</span>.  The <span style="font-family: monospace;">"median"</span> of an
  even number of images takes pixel nimages/2 + 1, where nimages is the
  number of images.
  </dd>
  </dl>
  <dl>
  <dt><b>low_reject = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 0' -->
  <dd>If the option is sum or average then when this parameter
  is less than 1 reject this fraction of low pixels from the sum or average
  otherwise reject this number of low pixels from the sum or average.
  </dd>
  </dl>
  <dl>
  <dt><b>high_reject = 0</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='high_reject' Line='high_reject = 0' -->
  <dd>If the option is sum or average then when this parameter
  is less than 1 reject this fraction of high pixels from the sum or average
  otherwise reject this number of high pixels from the sum or average.
  </dd>
  </dl>
  <dl>
  <dt><b>verbose = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no' -->
  <dd>Print a log of the operation?
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The input images are summed, averaged, or medianed pixel by pixel and the
  result recorded in the output image.  All input images must be the same
  size but not necessarily of the same pixel datatype.  For the sum or average
  option a selected fraction or number of pixels may be rejected.  The output
  option <span style="font-family: monospace;">"average"</span> divides the sum by the number of pixels in the sum.  The
  pixel datatype of the output image may be selected or defaulted to the
  calculation datatype. The calculation type may be selected or defaulted
  to the highest precedence datatype of the input images.  Note that a
  mixture of <span style="font-family: monospace;">"short"</span> and <span style="font-family: monospace;">"ushort"</span> images has a highest precedence datatype
  of <span style="font-family: monospace;">"int"</span>.  If all the image pixel datatypes are the same and agree with the
  calculation type then this operation is maximally efficient.  However,
  beware of integer overflows with images of datatype short or ushort.  A log
  of the task name, the input image names, the output image name, the output
  pixel datatype, the output option, and the pixel rejection parameters is
  printed when the verbose parameter is yes.
  </p>
  <p>
  In addition to summing the pixels the specified image header parameters may
  be summed or averaged.  This is primarily used for summing image exposure
  times.  No correction is made for rejected pixels.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. To sum three images:
  </p>
  <p>
  	im&gt; imsum frame1,frame2,frame3 sum hparams=<span style="font-family: monospace;">"itime,exposure"</span>
  </p>
  <p>
  2. To make a median image of a set of images:
  </p>
  <p>
  	im&gt; imsum obs* median option=median
  </p>
  <p>
  where <span style="font-family: monospace;">'*'</span> is a template wildcard.
  </p>
  <p>
  3. To reject the lowest and highest 2 pixels and average the rest:
  </p>
  <p>
  	im&gt; imsum obs* avg option=average low=2 high=2
  </p>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Revisions</h3>
  <!-- BeginSection: 'REVISIONS' -->
  <dl>
  <dt><b>IMSUM V2.11</b></dt>
  <!-- Sec='REVISIONS' Level=0 Label='IMSUM' Line='IMSUM V2.11' -->
  <dd>Now allows <span style="font-family: monospace;">"ushort"</span> data types.
  </dd>
  </dl>
  <!-- EndSection:   'REVISIONS' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <p>
  The following timings are for 512 x 512 short images in which the output
  image is also short and the calculation type is short.
  </p>
  <pre>
  	    OPERATION		      CPU(sec)
  	1. Sum of 3			 7.4
  	2. Average of 3			13.0
  	3. Median of 3			 9.9
  	4. Sum of 5			13.0
  	5. Median of 5			23.0
  	6. Sum of middle 3 of 5		45.5
  	7. Median of 7			77.8
  </pre>
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Notes</h3>
  <!-- BeginSection: 'NOTES' -->
  <p>
  Any number of images may be used.  However, there is a maximum number of
  images which may be open at one time.  If the number of images
  (of dimension &gt;= 2) exceeds this maximum and median or pixel rejection is
  used then the performance of this task will suffer due to the need to
  repeatedly open and close the excess images.  The maximum number is a
  configurable parameter in the include file <span style="font-family: monospace;">"imsum.h"</span>.
  </p>
  <p>
  This task has been largely replaced by the task <b>imcombine</b>.  It is
  still available but may be removed in the future.  <b>Imcombine</b> is
  specially designed to deal with the case of large numbers of images.
  </p>
  <!-- EndSection:   'NOTES' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <p>
  It is an error for the output image to have the same name as an
  existing image.  Beware of integer overflows when summing short images.
  </p>
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  imcombine
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'TIME REQUIREMENTS' 'NOTES' 'BUGS' 'SEE ALSO'  -->
  
