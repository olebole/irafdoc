ndprep — Make neutral density filter calibration image
======================================================

**Package: onedspec**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ndprep (Mar92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ndprep (Mar92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ndprep</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ndprep -- Make a neutral density filter calibration image
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  ndprep filter_curve output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_filter_curve">filter_curve</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter_curve' Line='filter_curve'>
  <DD>Neutral density filter curve.  The directory specified by the parameter
  <I>directory</I> is prepended to this name so if a directory is specified
  then it should not be given here.  If <TT>'?'</TT> a list of filter curves
  in the specified directory is typed.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>Output neutral density filter image.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_w0">w0   </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='w0' Line='w0   '>
  <DD>Starting wavelength for the output image in Angstroms.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dw">dw   </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dw' Line='dw   '>
  <DD>Wavelength increment for the output image in Angstroms.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nw">nw   </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nw' Line='nw   '>
  <DD>Number of wavelength points for the output image (i.e. the size of the
  output image).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nspace">nspace = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='nspace' Line='nspace = 0'>
  <DD>Number of spatial points for a two dimensional image.  If the value is
  zero then a one dimensional image is created.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logarithm">logarithm = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logarithm' Line='logarithm = no'>
  <DD>Use logarithmic wavelengths and intervals?  If yes then the wavelengths
  will have the same starting and ending points and number of pixels but
  the wavelength intervals will be logarithmic.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_flux">flux = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flux' Line='flux = yes'>
  <DD>Conserve flux when rebinning to logarithmic wavelength intervals?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dispaxis">dispaxis = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dispaxis' Line='dispaxis = 1'>
  <DD>Dispersion axis for two dimensional images.  Dispersion along the lines
  is 1 and dispersion along the columns is 2.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_directory">directory = "<TT>onedstds$ctio/</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='directory' Line='directory = "onedstds$ctio/"'>
  <DD>Directory containing neutral density filter curves.  This directory is
  prepended to the specified fiter curve file (and so must end with <TT>'/'</TT>
  or <TT>'$'</TT>).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  A neutral density (ND) filter curve is converted to a calibration image
  with the same size and wavelength range as the images to be calibrated.
  A list of standard neutral density curves is typed if the filter
  curve name is given as <TT>'?'</TT>.  The ND curves are text files containing
  wavelength and filter transmission pairs.  Comments begin with <TT>'#'</TT>.
  A plot of the ND curve can be obtained using <B>graph</B>.
  <P>
  The ND curve is first interpolated to a one dimensional image of
  <I>nw</I> wavelength points with starting wavelength <I>wO</I> and
  wavelength increment <I>dw</I> using the task <B>sinterp</B>.  The
  wavelength parameters must be in the same units as the filter curves
  (currently Angstroms) even if the final calibration image is to be in
  logarithmic wavelength intervals.  If logarithmic wavelength format
  is specified the image is rebinned over the same wavelength range with
  the same number of points using the task <B>dispcor</B>.  The rebinning
  may include flux conservation to account for the changing size of
  pixels or simply interpolate.  Note that flux conservation will
  change the apparent shape of the ND curve.
  <P>
  If the number of points across the dispersion, <I>nspace</I> is zero then
  the final calibration image is one dimensional.  If it is greater than
  zero the one dimensional ND image is expanded to the specified number
  of spatial points with the dispersion axis specified by the parameter
  <I>dispaxis</I> (1 = dispersion along the lines, 2 = dispersion along
  the columns).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To get a list of standard ND filter curves:
  <P>
  	cl&gt; ndprep ?
  <P>
  To graph the ND filter curve:
  <P>
  	cl&gt; graph onedstds$ctio/nd1m.100mag.dat
  <P>
  Naturally, if a calibration image is made then the image plotting tasks
  such as <B>graph</B>, <B>implot</B>, and <B>splot</B> may also be used.
  <P>
  To make a one dimensional ND calibration spectrum:
  <P>
  <PRE>
  	cl&gt; ndprep w0=4000 dw=1.2 nw=512
  	Input ND filter curve:  onedstds$ctio/nd1m.100mag.dat
  	Output calibration image: NDimage
  </PRE>
  <P>
  To make a two dimensional ND calibration spectrum in logarithmic wavelength:
  <P>
  <PRE>
  	cl&gt; ndprep w0=4000 dw=1.2 nw=512 nspace=200 log+
  	Input ND filter curve:  onedstds$ctio/nd4m.u000mag.dat
  	Output calibration image: NDimage
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_NDPREP">NDPREP V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='NDPREP' Line='NDPREP V2.10'>
  <DD>This task was moved from the <B>proto</B> package.  It was originally
  written at CTIO for CTIO data.  It's functionality is largely unchanged
  though it has been updated for changes in the <B>onedspec</B> package.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  sinterp, dispcor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>