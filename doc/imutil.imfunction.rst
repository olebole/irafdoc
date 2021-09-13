.. _imfunction:

imfunction — Apply a single argument function to a list of images
=================================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  imfunction -- Apply a function to the image pixel values
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage	</H3>
  <! BeginSection: 'USAGE	'>
  <UL>
  imfunction input output function
  </UL>
  <! EndSection:   'USAGE	'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The input image list.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output image list. The number of output images must match the number of
  input images. If the output image list equals the input image list
  the input images are overwritten.
  </DD>
  </DL>
  <DL>
  <DT><B>function</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function'>
  <DD>Function to be applied to the input pixels. The options are:
  <DL>
  <DT><B>log10</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='log10' Line='log10'>
  <DD>Take the logarithm to base 10 of an image. Negative and zero-valued
  pixels will be assigned the value -MAX_EXPONENT.
  </DD>
  </DL>
  <DL>
  <DT><B>alog10</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='alog10' Line='alog10'>
  <DD>Taken the antilogarithm to base 10 of the image. Positive out-of-bounds
  pixel values will be assigned the value MAX_REAL, negative out-of-bounds
  pixel values will be assigned the value 0.0.
  </DD>
  </DL>
  <DL>
  <DT><B>ln   </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ln' Line='ln   '>
  <DD>Take the natural logarithm of an image. Negative and zero-valued pixels
  will be assigned the value - ln (10.) * MAX_EXPONENT.
  </DD>
  </DL>
  <DL>
  <DT><B>aln   </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='aln' Line='aln   '>
  <DD>Take the antilogarithm to base e of an image. Positive out-of-bounds pixel
  values will be assigned the value MAX_REAL, negative out-of-bounds
  pixel values will be assigned the value 0.0
  </DD>
  </DL>
  <DL>
  <DT><B>sqrt</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sqrt' Line='sqrt'>
  <DD>Take the square root of an image. Negative pixel values will be assigned
  the value 0.0.
  </DD>
  </DL>
  <DL>
  <DT><B>square</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='square' Line='square'>
  <DD>Take the square of an image.
  </DD>
  </DL>
  <DL>
  <DT><B>cbrt</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='cbrt' Line='cbrt'>
  <DD>Take the cube root of an image.
  </DD>
  </DL>
  <DL>
  <DT><B>cube</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='cube' Line='cube'>
  <DD>Take the cube of an image.
  </DD>
  </DL>
  <DL>
  <DT><B>abs  </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='abs' Line='abs  '>
  <DD>Take the absolute value of an image.
  </DD>
  </DL>
  <DL>
  <DT><B>neg  </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='neg' Line='neg  '>
  <DD>Take the negative of an image.
  </DD>
  </DL>
  <DL>
  <DT><B>cos  </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='cos' Line='cos  '>
  <DD>Take the cosine of an image.
  </DD>
  </DL>
  <DL>
  <DT><B>sin  </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='sin' Line='sin  '>
  <DD>Take the sine of an image.
  </DD>
  </DL>
  <DL>
  <DT><B>tan  </B></DT>
  <! Sec='PARAMETERS' Level=1 Label='tan' Line='tan  '>
  <DD>Take the tangent of an image.
  </DD>
  </DL>
  <DL>
  <DT><B>acos</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='acos' Line='acos'>
  <DD>Take the arc-cosine of an image. The output pixels will lie between
  0.0 and PI.
  </DD>
  </DL>
  <DL>
  <DT><B>asin</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='asin' Line='asin'>
  <DD>Take the arc-sine of an image. The output pixels will lie between -PI/2
  and +PI/2.
  </DD>
  </DL>
  <DL>
  <DT><B>atan</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='atan' Line='atan'>
  <DD>Take the arc-tangent of an image. The output pixels will lie between
  -PI/2 and +PI/2.
  </DD>
  </DL>
  <DL>
  <DT><B>hcos</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='hcos' Line='hcos'>
  <DD>Take the hyperbolic cosine of an image. Positive or negative
  out-of-bounds pixels will be assigned the value MAX_REAL.
  </DD>
  </DL>
  <DL>
  <DT><B>hsin</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='hsin' Line='hsin'>
  <DD>Take the hyperbolic sine of an image. Positive and negative out-of-bounds
  pixel values will be assigned the values MAX_REAL and -MAX_REAL respectively.
  </DD>
  </DL>
  <DL>
  <DT><B>htan</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='htan' Line='htan'>
  <DD>Take the hyperbolic tangent of an image.
  </DD>
  </DL>
  <DL>
  <DT><B>reciprocal</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reciprocal' Line='reciprocal'>
  <DD>Take the reciprocal of an image. Zero-valued pixels will be assigned
  the output value 0.0
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print messages about actions taken by the task?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  The selected function <I>function</I> is applied to the pixel values of all
  the input images <I>input</I> to create the pixel values of the output
  images <I>output</I>. The number of output images must equal the number of
  input images. If the output image name is the same as the input image name
  the input image will be overwritten.
  <P>
  If the input image is type real or double the output image will
  be of type real or double respectively. If the input image is type
  ushort then the output image will be type real. If the input image is one of
  the remaining integer data types, then the output image will be type
  real, unless function is "<TT>abs</TT>" or "<TT>neg</TT>", in which case the output
  data type will be the same as the input data type.
  <P>
  Values of the machine dependent constants MAX_REAL and MAX_EXPONENT can be
  found in the file "<TT>hlib$mach.h</TT>". 
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Take the logarithm of the pixel values of images in1 and in2 and write
  the results to out1 and out2.
  <P>
  <PRE>
      cl&gt; imfunction in1,in2 out1,out2 log10
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  imarith,imreplace
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE	' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
