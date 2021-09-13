.. _imsum:

imsum — Compute the sum, average, or median of a set of images
==============================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imsum -- sum, average, or median images
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  imsum input output
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>Input images.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output image.
  </DD>
  </DL>
  <DL>
  <DT><B>title = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='title' Line='title = ""'>
  <DD>Image title for the output image.  If null ("<TT></TT>") then the title of the
  first image is used.
  </DD>
  </DL>
  <DL>
  <DT><B>hparams = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='hparams' Line='hparams = ""'>
  <DD>List of image header parameters to be summed or averaged.  This feature
  is only used when summing or averaging and no correction is made for
  rejected pixels.  It is primarily used to sum exposure times.
  </DD>
  </DL>
  <DL>
  <DT><B>pixtype = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pixtype' Line='pixtype = ""'>
  <DD>Pixel datatype for the output image.  The pixel datatypes are "<TT>double</TT>",
  "<TT>real</TT>", "<TT>long</TT>", "<TT>integer</TT>", "<TT>ushort</TT>", and "<TT>short</TT>" in order of precedence.
  If null ("<TT></TT>") then the calculation type is used.
  The datatypes may be abbreviated to a single character.
  </DD>
  </DL>
  <DL>
  <DT><B>calctype = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='calctype' Line='calctype = ""'>
  <DD>Calculation type.  The calculation types are "<TT>double</TT>", "<TT>real</TT>", "<TT>long</TT>",
  "<TT>integer</TT>", and "<TT>short</TT>" in order of precedence.  If null ("<TT></TT>") then the
  highest precedence datatype of the input images is used.
  If there is a mixture of "<TT>short</TT>" and "<TT>ushort</TT>" images then the highest
  precedence datatype will be "<TT>int</TT>".
  The calculation types may be abbreviated to a single character.
  </DD>
  </DL>
  <DL>
  <DT><B>option = "<TT>sum</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='option' Line='option = "sum"'>
  <DD>Output options are "<TT>sum</TT>", "<TT>average</TT>", or "<TT>median</TT>".  The "<TT>median</TT>" of an
  even number of images takes pixel nimages/2 + 1, where nimages is the
  number of images.
  </DD>
  </DL>
  <DL>
  <DT><B>low_reject = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='low_reject' Line='low_reject = 0'>
  <DD>If the option is sum or average then when this parameter
  is less than 1 reject this fraction of low pixels from the sum or average
  otherwise reject this number of low pixels from the sum or average.
  </DD>
  </DL>
  <DL>
  <DT><B>high_reject = 0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='high_reject' Line='high_reject = 0'>
  <DD>If the option is sum or average then when this parameter
  is less than 1 reject this fraction of high pixels from the sum or average
  otherwise reject this number of high pixels from the sum or average.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print a log of the operation?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The input images are summed, averaged, or medianed pixel by pixel and the
  result recorded in the output image.  All input images must be the same
  size but not necessarily of the same pixel datatype.  For the sum or average
  option a selected fraction or number of pixels may be rejected.  The output
  option "<TT>average</TT>" divides the sum by the number of pixels in the sum.  The
  pixel datatype of the output image may be selected or defaulted to the
  calculation datatype. The calculation type may be selected or defaulted
  to the highest precedence datatype of the input images.  Note that a
  mixture of "<TT>short</TT>" and "<TT>ushort</TT>" images has a highest precedence datatype
  of "<TT>int</TT>".  If all the image pixel datatypes are the same and agree with the
  calculation type then this operation is maximally efficient.  However,
  beware of integer overflows with images of datatype short or ushort.  A log
  of the task name, the input image names, the output image name, the output
  pixel datatype, the output option, and the pixel rejection parameters is
  printed when the verbose parameter is yes.
  <P>
  In addition to summing the pixels the specified image header parameters may
  be summed or averaged.  This is primarily used for summing image exposure
  times.  No correction is made for rejected pixels.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To sum three images:
  <P>
  	im&gt; imsum frame1,frame2,frame3 sum hparams="<TT>itime,exposure</TT>"
  <P>
  2. To make a median image of a set of images:
  <P>
  	im&gt; imsum obs* median option=median
  <P>
  where <TT>'*'</TT> is a template wildcard.
  <P>
  3. To reject the lowest and highest 2 pixels and average the rest:
  <P>
  	im&gt; imsum obs* avg option=average low=2 high=2
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Revisions</H3>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B>IMSUM V2.11</B></DT>
  <! Sec='REVISIONS' Level=0 Label='IMSUM' Line='IMSUM V2.11'>
  <DD>Now allows "<TT>ushort</TT>" data types.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  The following timings are for 512 x 512 short images in which the output
  image is also short and the calculation type is short.
  <P>
  <PRE>
  	    OPERATION		      CPU(sec)
  	1. Sum of 3			 7.4
  	2. Average of 3			13.0
  	3. Median of 3			 9.9
  	4. Sum of 5			13.0
  	5. Median of 5			23.0
  	6. Sum of middle 3 of 5		45.5
  	7. Median of 7			77.8
  </PRE>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Notes</H3>
  <! BeginSection: 'NOTES'>
  <UL>
  Any number of images may be used.  However, there is a maximum number of
  images which may be open at one time.  If the number of images
  (of dimension &gt;= 2) exceeds this maximum and median or pixel rejection is
  used then the performance of this task will suffer due to the need to
  repeatedly open and close the excess images.  The maximum number is a
  configurable parameter in the include file "<TT>imsum.h</TT>".
  <P>
  This task has been largely replaced by the task <B>imcombine</B>.  It is
  still available but may be removed in the future.  <B>Imcombine</B> is
  specially designed to deal with the case of large numbers of images.
  </UL>
  <! EndSection:   'NOTES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  It is an error for the output image to have the same name as an
  existing image.  Beware of integer overflows when summing short images.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imcombine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'TIME REQUIREMENTS' 'NOTES' 'BUGS' 'SEE ALSO'  >
  
