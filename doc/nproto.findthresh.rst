findthresh — Estimate a CCD's sky noise from the gain and readnoise
===================================================================

**Package: nproto**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>findthresh (Apr92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.nproto</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>findthresh (Apr92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>findthresh</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  findthresh -- Estimate the background noise level of a CCD
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  findthresh data
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_data">data</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='data' Line='data'>
  <DD>The level of the sky (or any other data level, for that matter) in A/D
  units, for which the random error is to be estimated.  If this is not
  given on the command line and a list of <B>images</B> is specified then
  the data level will be measured from the images.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_images">images = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images = ""'>
  <DD>If not NULL ("<TT></TT>") and if <B>data</B> is not specified, this is a list of
  images whose random background error per pixel is to be estimated.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_section">section = "<TT>[*,*]</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = "[*,*]"'>
  <DD>The selected image section for the statistics.  This should be chosen
  to exclude bad columns or rows, cosmic rays, and other blemishes.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_gain">gain</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='gain' Line='gain'>
  <DD>The CCD gain in electrons/ADU.
  This may be estimated using the FINDGAIN task.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_readnoise">readnoise</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='readnoise' Line='readnoise'>
  <DD>The CCD read noise in electrons.
  This may be estimated using the FINDGAIN task.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nframes">nframes = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nframes' Line='nframes = 1'>
  <DD>The number of raw data frames that were coadded or averaged
  to produce the <B>images</B>.  If this is not set to 1, the
  <B>coaddtype</B> parameter must also be set to the proper value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coaddtype">coaddtype = "<TT>average</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coaddtype' Line='coaddtype = "average"'>
  <DD>For coadded frames (<B>nframes</B> &gt; 1) the type of combination
  that was done, either "<TT>average</TT>" or "<TT>sum</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_center">center = "<TT>mean</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='center' Line='center = "mean"'>
  <DD>The statistical measure of central tendency that is used to estimate
  the data level of each image.  This can have the values:  <B>mean</B>,
  <B>midpt</B>, or <B>mode</B>.  These are calculated using the same
  algorithm as the IMSTATISTICS task.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_binwidth">binwidth = 0.1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='binwidth' Line='binwidth = 0.1'>
  <DD>The bin width of the histogram (in sigma) that is used to estimate the
  <B>midpt</B> or <B>mode</B> of the data section in each image.
  The default case of center=<B>mean</B> does not use this parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Label the computed and measured background noise on output,
  rather than print them two per line?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  FINDTHRESH can be used to estimate the expected random error per pixel
  (in ADU) of the sky background of a CCD image, given the <B>gain</B> (in
  electrons per ADU) and <B>readnoise</B> (in electrons) of the CCD.  The
  sky background (or any other data level of interest) can be specified
  directly with the <B>data</B> parameter, or the representative values can
  be measured from a specified list of <B>images</B> as also governed by
  the <B>section</B>, <B>center</B>, and <B>binwidth</B> parameters.
  FINDTHRESH can be used with processed frames that are the coaddition or
  average of several raw images by choosing the correct values for the
  <B>nframes</B> and <B>coaddtype</B> parameters.  In this case
  (<B>nframes</B> &gt; 1), the effective gain and effective readnoise of the
  coadded frames will also be printed out.
  <P>
  The section over which the statistics of the <B>images</B> are computed
  should be chosen carefully.  The frames may be displayed and perhaps
  blinked, and IMSTATISTICS, IMHISTOGRAM, IMPLOT, and other tasks may be
  used to compare the statistics of various sections of the images directly.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_algorithm">ALGORITHM</A></H2>
  <! BeginSection: 'ALGORITHM'>
  <UL>
  The formula used by the task is:
  <P>
  <PRE>
      random error in 1 pixel = sqrt (data*p(N) + r(N)**2) / p(N)
  </PRE>
  <P>
  Where the effective gain, p(N), is given in electrons per ADU and
  the effective readnoise, r(N), is given in electrons.  The effective
  gain and readnoise are calculated from the intrinsic <B>gain</B> and
  <B>readnoise</B>, specified as parameters to the task, by the relations:
  <P>
  <PRE>
      p(N) =      N  * <B>gain</B>        (only if the frames were <B>averaged</B>)
      r(N) = sqrt(N) * <B>readnoise</B>   (whether averaged <B>or</B> summed frames)
  </PRE>
  <P>
  In our implementation, the level of the sky can be calculated using any
  of the <B>mean</B>, <B>midpt</B> (an estimate of the median), or <B>mode</B>
  as determined by the <B>center</B> parameter.  For the <B>midpt</B> or
  <B>mode</B> choices only, the value of the <B>binwidth</B> parameter
  determines the bin width (in sigma) of the histogram that is used in
  the calculation.  FINDTHRESH uses the IMSTATISTICS task to measure the
  statistics.
  </UL>
  <! EndSection:   'ALGORITHM'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To estimate the CCD background noise at a specified data level, gain and
  readnoise (note that you will be prompted for the gain and the readnoise
  if you don't set them either explicitly on the command line, or previously
  using, for example, eparam):
  <P>
  <PRE>
      lo&gt; findthresh 100 gain=2.3 readnoise=13.
  </PRE>
  <P>
  To estimate the CCD background noise within a 100x100 section
  of a list of images, data*.imh:
  <P>
  <PRE>
      lo&gt; findthresh data*.imh section="[271:370,361:460]"
  </PRE>
  <P>
  To estimate the CCD background noise using the mode to estimate the
  sky level for each image section:
  <P>
  <PRE>
      lo&gt; findthresh.section="[271:370,361:460]"
      lo&gt; findthresh data*.imh center=mode
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  findgain, imstatistics, imhistogram
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'ALGORITHM' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>