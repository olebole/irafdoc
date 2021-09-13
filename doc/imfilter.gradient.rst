gradient — Convolve a list of 1 or 2-D images with a gradient operator
======================================================================

**Package: imfilter**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>gradient (Nov85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>images.imfilter</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>gradient (Nov85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>gradient</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  gradient -- convolve a list of images with the gradient filter
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  gradient input output gradient
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of images for which gradient images are to be calculated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of output images. The number of output images must equal the number of
  input images. If the input image name equals the output image name the
  convolved image will replace the input image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gradient">gradient</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gradient' Line='gradient'>
  <DD>The gradient filters are a set of 8 three by three kernels identified by the
  angle of maximum response as measured counter-clockwise to the x axis. The
  kernels approximate the gradient operator, which is defined as the slope of
  the intensity distribution in an image.  The eight supported gradient
  operators are listed below.
  <DL>
  <DT><B><A NAME="l_">"<TT>0</TT>", "<TT>180</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"0", "180"'>
  <DD>Calculate the gradient image along a 0 or 180 degree angle.
  These options approximate the d/dx operator.
  Option "<TT>0</TT>" produces a maximum response for pixel values which
  increase with increasing x, whereas option "<TT>180</TT>" produces a maximum
  response for pixel values which decrease with increasing x. 
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>90</TT>", "<TT>270</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"90", "270"'>
  <DD>Calculate the gradient image along a 90 or 270 degree angle.
  These options approximate the d/dy operator.
  Option "<TT>90</TT>" produces a maximum response for pixel values which
  increase with increasing y, whereas option "<TT>270</TT>" produces a maximum
  response for pixel values which decrease with increasing y.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>45</TT>", "<TT>225</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"45", "225"'>
  <DD>Calculate the gradient image along a 45 or 225 degree angle.
  Option "<TT>45</TT>" produces a maximum response for pixel values which increase
  along a line at 45 degrees counter-clockwise to the x axis.
  Option "<TT>225</TT>" produces
  a maximum response for pixel values which increase along a line at 225
  degrees to the x axis.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">"<TT>135</TT>", "<TT>315</TT>" </A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='"135", "315" '>
  <DD>Calculate the gradient image along a 135 or 315 degree angle.
  Option "<TT>135</TT>" produces a maximum response for pixel values which increase
  along a line at 135 degrees counter-clockwise to the x axis.
  Option "<TT>315</TT>" produces
  a maximum response for pixel values which increase along a line at 315
  degrees to the x axis.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_boundary">boundary = "<TT>nearest</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='boundary' Line='boundary = "nearest"'>
  <DD>The algorithm used to compute the values of out of bounds pixels. The 
  options are:
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Use the value of the nearest boundary pixel.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='constant' Line='constant'>
  <DD>Use a constant value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reflect">reflect</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='reflect' Line='reflect'>
  <DD>Generate a value by reflecting around the boundary.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_wrap">wrap</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='wrap' Line='wrap'>
  <DD>Generate a value by wrapping around to the opposite side of the image.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_constant">constant = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='constant' Line='constant = 0.'>
  <DD>The constant for constant-valued boundary extension.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  GRADIENT convolves the list of images specified by <I>input</I> with one of
  eight three by three gradient kernels specified by <I>gradient</I> 
  and places the output images in <I>output</I>.
  If the image names in <I>output</I> equal the image names in <I>input</I> the
  gradient operation is performed in place and the original images are
  overwritten. Out of bounds pixels are computed using the algorithm
  specified by <I>boundary</I>.
  <P>
  GRADIENT acts like a simple edge detector or high pass filter which is sensitive
  to both the magnitude and direction of changes in intensity in an image.
  For example, if an image's pixel values are specified by the sum of their
  x and y coordinates (z = x + y) and boundary extension effects are ignored,
  the "<TT>0</TT>", "<TT>45</TT>", "<TT>90</TT>", "<TT>135</TT>", "<TT>180</TT>", "<TT>225</TT>", "<TT>270</TT>", and "<TT>315</TT>" gradient kernels
  will each produce a constant image containing the numbers 1, sqrt (2), 1, 0,
  -1, -sqrt (2), -1, and 0 respectively. 
  <P>
  The eight gradient filters are listed below. The I[*,*] are the elements of
  the input image and the O[*,*] are elements of the output image.
  <P>
  <PRE>
                           0
  <P>
  	    - I[-1,1]          + 0*I[0,1]  + I[1,1]
     O[0,0] = - I[-1,0]*sqrt(2)  + 0*I[0,0]  + I[1,0] * sqrt(2)  
  	    - I[-1,-1]         + 0*I[0,-1] + I[-1,-1]
  <P>
  			45
  	     
  	    + I[-1,1]*0          + I[0,1]   + I[1,1]/2/sqrt(2)
     O[0,0] = - I[-1,0]            + I[0,0]*0 + I[1,0] 
              - I[-1,-1]/2/sqrt(2) - I[0,-1]  + I[1,-1]*0 
  <P>
  			90
  	     
  	    + I[-1,1]    + I[0,1]*sqrt(2)  + I[1,1]
     O[0,0] = + I[-1,0]*0  + I[0,0]*0        + I[1,0]
  	    - I[-1,-1]   - I[0,-1]*sqrt(2) - I[-1,-1]
  <P>
  		       135
  <P>
  	    + I[-1,1]/2/sqrt(2) + I[0,1]   + I[1,1]*0
     O[0,0] = + I[-1,0]           + I[0,0]*0 - I[1,0]
              + I[-1,-1]*0        - I[0,-1]  - I[1,-1]/2/sqrt(2) 
  <P>
  			180
  <P>
  	    + I[-1,1]          + 0*I[0,1]  - I[1,1]
     O[0,0] = + I[-1,0]*sqrt(2)  + 0*I[0,0]  - I[1,0]*sqrt(2)
  	    + I[-1,-1]         + 0*I[0,-1] - I[-1,-1]
  <P>
  		       225
  <P>
  	    + I[-1,1]*0          - I[0,1]   - I[1,1]/2/sqrt(2)
     O[0,0] = + I[-1,0]            + I[0,0]*0 - I[1,0]
              + I[-1,-1]/2/sqrt(2) + I[0,-1]  + I[1,-1]*0 
  <P>
  		       270
  <P>
  	    - I[-1,1]    - I[0,1]*sqrt(2)  - I[1,1]
     O[0,0] = + I[-1,0]*0  + I[0,0]*0        + I[1,0]*0
  	    + I[-1,-1]   + I[0,-1]*sqrt(2) + I[-1,-1]
  <P>
  		      315
  <P>
  	    - I[-1,1]/2/sqrt(2) - I[0,1]   + I[1,1]*0
     O[0,0] = - I[-1,0]           + I[0,0]*0 + I[1,0]
              + I[-1,-1]*0        + I[0,-1]  + I[1,-1]/2/sqrt(2) 
  <P>
  </PRE>
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Calculate the gradient in the 180 degree direction using nearest neighbor
     boundary extension.
  <P>
  <PRE>
      cl&gt; gradient m83 m83.odeg 180
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  <P>
  GRADIENT requires approximately 2.0 cpu seconds to convolve a
  512 square real image with a 3 by 3 gradient kernel on a Sparc Station 1.
  <P>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  <P>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  convolve, gauss, laplace, boxcar
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>