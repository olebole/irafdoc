zerocombine — Combine and process zero level images
===================================================

**Package: ccdred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>zerocombine (Aug91)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.ccdred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>zerocombine (Aug91)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>zerocombine</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  zerocombine -- Combine and process zero level images
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  zerocombine input
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of zero level images to combine.  The <I>ccdtype</I> parameter
  may be used to select the zero level images from a list containing all
  types of data.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output = "<TT>Zero</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output = "Zero"'>
  <DD>Output zero level root image name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_combine">combine = "<TT>average</TT>" (average|median)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='combine' Line='combine = "average" (average|median)'>
  <DD>Type of combining operation performed on the final set of pixels (after
  rejection).  The choices are
  "<TT>average</TT>" or "<TT>median</TT>".  The median uses the average of the two central
  values when the number of pixels is even.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reject">reject = "<TT>minmax</TT>" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reject' Line='reject = "minmax" (none|minmax|ccdclip|crreject|sigclip|avsigclip|pclip)'>
  <DD>Type of rejection operation.  See <B>combine</B> for details.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ccdtype">ccdtype = "<TT>zero</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccdtype' Line='ccdtype = "zero"'>
  <DD>CCD image type to combine.  If no image type is given then all input images
  are combined.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_process">process = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='process' Line='process = no'>
  <DD>Process the input images before combining?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_delete">delete = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='delete' Line='delete = no'>
  <DD>Delete input images after combining?  Only those images combined are deleted.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_clobber">clobber = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='clobber' Line='clobber = no'>
  <DD>Clobber existing output images?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_scale">scale = "<TT>none</TT>" (none|mode|median|mean|exposure)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='scale' Line='scale = "none" (none|mode|median|mean|exposure)'>
  <DD>Multiplicative image scaling to be applied.  The choices are none, scale
  by the mode, median, or mean of the specified statistics section, or scale
  by the exposure time given in the image header.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_statsec">statsec = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='statsec' Line='statsec = ""'>
  <DD>Section of images to use in computing image statistics for scaling.
  If no section is given then the entire region of the image is
  sampled (for efficiency the images are sampled if they are big enough).
  </DD>
  </DL>
  <P>
  <CENTER>Algorithm Parameters
  
  </CENTER><BR>
  <DL>
  <DT><B><A NAME="l_nlow">nlow = 0,  nhigh = 1 (minmax)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nlow' Line='nlow = 0,  nhigh = 1 (minmax)'>
  <DD>The number of low and high pixels to be rejected by the "<TT>minmax</TT>" algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nkeep">nkeep = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nkeep' Line='nkeep = 1'>
  <DD>The minimum number of pixels to retain or the maximum number to reject
  when using the clipping algorithms (ccdclip, crreject, sigclip,
  avsigclip, or pclip).  When given as a positive value this is the minimum
  number to keep.  When given as a negative value the absolute value is
  the maximum number to reject.  This is actually converted to a number
  to keep by adding it to the number of images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mclip">mclip = yes (ccdclip, crreject, sigclip, avsigcliip)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='mclip' Line='mclip = yes (ccdclip, crreject, sigclip, avsigcliip)'>
  <DD>Use the median as the estimate for the true intensity rather than the
  average with high and low values excluded in the "<TT>ccdclip</TT>", "<TT>crreject</TT>",
  "<TT>sigclip</TT>", and "<TT>avsigclip</TT>" algorithms?  The median is a better estimator
  in the presence of data which one wants to reject than the average.
  However, computing the median is slower than the average.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lsigma">lsigma = 3., hsigma = 3. (ccdclip, crreject, sigclip, avsigclip, pclip)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lsigma' Line='lsigma = 3., hsigma = 3. (ccdclip, crreject, sigclip, avsigclip, pclip)'>
  <DD>Low and high sigma clipping factors for the "<TT>ccdclip</TT>", "<TT>crreject</TT>", "<TT>sigclip</TT>",
  "<TT>avsigclip</TT>", and "<TT>pclip</TT>" algorithms.  They multiply a "<TT>sigma</TT>" factor
  produced by the algorithm to select a point below and above the average or
  median value for rejecting pixels.  The lower sigma is ignored for the
  "<TT>crreject</TT>" algorithm.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rdnoise">rdnoise = "<TT>0.</TT>", gain = "<TT>1.</TT>", snoise = "<TT>0.</TT>" (ccdclip, crreject)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rdnoise' Line='rdnoise = "0.", gain = "1.", snoise = "0." (ccdclip, crreject)'>
  <DD>CCD readout noise in electrons, gain in electrons/DN, and sensitivity noise
  as a fraction.  These parameters are used with the "<TT>ccdclip</TT>" and "<TT>crreject</TT>"
  algorithms.  The values may be either numeric or an image header keyword
  which contains the value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_pclip">pclip = -0.5 (pclip)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pclip' Line='pclip = -0.5 (pclip)'>
  <DD>Percentile clipping algorithm parameter.  If greater than
  one in absolute value then it specifies a number of pixels above or
  below the median to use for computing the clipping sigma.  If less
  than one in absolute value then it specifies the fraction of the pixels
  above or below the median to use.  A positive value selects a point
  above the median and a negative value selects a point below the median.
  The default of -0.5 selects approximately the quartile point.
  See <B>combine</B> for further details.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_blank">blank = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='blank' Line='blank = 0.'>
  <DD>Output value to be used when there are no pixels.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The zero level images in the input image list are combined.
  The input images may be processed first if desired.
  The original images may be deleted automatically if desired.
  The output pixel datatype will be real.
  <P>
  This task is a script which applies <B>ccdproc</B> and <B>combine</B>.  The
  parameters and combining algorithms are described in detail in the help for
  <B>combine</B>.  This script has default parameters specifically set for
  zero level images and simplifies the combining parameters.  There are other
  combining options not included in this task.  For these additional
  features, such as thresholding, offseting, masking, and projecting, use
  <B>combine</B>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The image data contains four zero level images.
  To automatically select them and combine them as a background job
  using the default combining algorithm:
  <P>
      cl&gt; zerocombine ccd*.imh&amp;
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ccdproc, combine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>