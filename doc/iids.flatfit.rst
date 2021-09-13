flatfit — Sum and normalize flat field spectra
==============================================

**Package: iids**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>flatfit (Dec86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.iids/noao.imred.irs</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>flatfit (Dec86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>flatfit</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  flatfit -- Sum and normalize flat field spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  flatfit root records
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_root">root</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='root' Line='root'>
  <DD>The root file name for the input names of the flat field
  spectra to be accumulated and fit for normalization.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records'>
  <DD>The range of spectra indicating the elements of the string.
  The names of the spectra will be formed by appending the range
  elements to the input root name.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>This is the root file name for the names of the spectra which will
  be created during normalization. The aperture number for the observation
  will be appended to the root in form "<TT>root.nnnn</TT>" where nnnn is the aperture
  number with leading 0's.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_function">function = "<TT>chebyshev</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='function' Line='function = "chebyshev"'>
  <DD>The accumulated spectra are fit by this function type - either
  chebyshev or legendre polynomials, or spline3 or spline1 interpolators.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_order">order = 4</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='order' Line='order = 4'>
  <DD>The order of the fit using the above function. This should generally be
  a low order fit to avoid introduction of high spatial frequency wiggles.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_niter">niter = 1</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='niter' Line='niter = 1'>
  <DD>The number of iterations to reject discrepant pixels upon initial
  startup of the solution.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_lower">lower = 2.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='lower' Line='lower = 2.0'>
  <DD>The number of sigmas for which data values less than this cutoff are
  rejected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_upper">upper = 2.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='upper' Line='upper = 2.0'>
  <DD>The number of sigmas for which data values greater than this cutoff are
  rejected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ngrow">ngrow = 0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ngrow' Line='ngrow = 0'>
  <DD>The number of pixels on either side of a rejected pixel to also be rejected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_div_min">div_min = 1.0</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='div_min' Line='div_min = 1.0'>
  <DD>During the normalization process, a division by zero will produce
  this value as a result.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interact">interact = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='interact' Line='interact = yes'>
  <DD>If set to yes, graphical interaction with the normalization process
  is provided for at least the first aperture for which sums are available.
  If set to no, no interaction is provided.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_all_interact">all_interact = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='all_interact' Line='all_interact = no'>
  <DD>If set to yes, then interaction will be provided for all apertures
  for which sums have been accumulated. If set to no then the parameter interact
  will determine if the first aperture data is to be interactive.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_coincor">coincor = )_.coincor</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='coincor' Line='coincor = )_.coincor'>
  <DD>If set to yes, coincidence correction is applied to the data during
  the summation process, and the following three parameters are required.
  See <B>coincor</B> for more about this correction.
  <DL>
  <DT><B><A NAME="l_ccmode">ccmode = )_.ccmode</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ccmode' Line='ccmode = )_.ccmode'>
  <DD>The mode by which the coincidence correction is to be performed.
  This may be "<TT>iids</TT>" or "<TT>photo</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_deadtime">deadtime = )_.deadtime</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='deadtime' Line='deadtime = )_.deadtime'>
  <DD>The detector deadtime in seconds.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_power">power = )_.power</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='power' Line='power = )_.power'>
  <DD>Power law IIDS non-linear correction exponent.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cursor">cursor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cursor' Line='cursor = ""'>
  <DD>Graphics cursor input.  When null the standard cursor is used otherwise
  the specified file is used.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The specified spectra are added by aperture number to produce
  summations which are then fit by a specified fitting function.
  The fitting function is then divided into the sum to produce a
  normalized (to 1.0) sum in which the low frequency spatial
  response has been removed.
  <P>
  The resultant normalized images may then be divided into all other
  data to remove the pixel-to-pixel variations without introducing
  any color terms. The spectra may be used directly if they happen
  to be object spectra in which the low frequency response is to be
  removed.
  <P>
  During the accumulation process the spectra may be corrected for
  coincidence losses if the detector is subject to the phenomenon.
  <P>
  After accumulating all input spectra, the pixels in each sum are
  fit according to
  the specified function. If the interactive switches are set, then
  graphical interaction is made available. If only the interact parameter
  is set to yes, then only the data from the first aperture will
  be available for interaction. Data from subsequent apertures will
  be fit using the same parameters and number of iterations as the
  first. If the all_interact parameter is also
  set, then data from each aperture will be presented for interaction.
  <P>
  At each step in the fit, pixels which are discrepant by more than
  "<TT>upper</TT>" sigmas above the fit, or "<TT>lower</TT>" sigmas below the fit, are
  rejected. The rejection process may be applied many times (iterations)
  to continue rejecting pixels. If the upper and lower sigmas are
  not equal, the resulting fit will be biased slightly above the mean
  (for lower &lt; upper) or below the mean (upper &lt; lower). This is useful
  when the spectrum being fit is that of a star having either absorption
  or emission lines.
   
  A display is presented of the sum and the fit through the data.
  A status line is printed containing the fit type, the order of
  the fit, the rms residual from the fit, and the number of data
  points in the fit after one iteration of rejection.
  <P>
  The following cursor keystrokes are then active:
  <DL>
  <DT><B><A NAME="l_">?</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='?'>
  <DD>Clear the screen and display the active keystrokes
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">/</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='/'>
  <DD>Indicate active keystrokes on the status line
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_e">e</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='e' Line='e'>
  <DD>Change plot mode to an error plot. This display is defined
  as the deviation from the fit divided by the data values [ (data - fit)/ data]
  at each pixel
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_f">f</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='f' Line='f'>
  <DD>Change plot mode back to the fit through the data display
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_o">o</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='o' Line='o'>
  <DD>Change the order of the fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_l">l</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='l' Line='l'>
  <DD>Change the lower rejection criterion (in units of sigma).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_u">u</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='u' Line='u'>
  <DD>Change the upper rejection criterion.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_s">s</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='s' Line='s'>
  <DD>Change both rejection criteria to the same value.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_r">r</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='r' Line='r'>
  <DD>Reinstate rejected pixels.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_i">i</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='i' Line='i'>
  <DD>Iterate one more time.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_n">n</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='n' Line='n'>
  <DD>Iterate several more times - the user is prompted for the count.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_q">q</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='q' Line='q'>
  <DD>Quit and accept the solution
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_">&lt;CR&gt;</A></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line='&lt;CR&gt;'>
  <DD>RETURN is the same as <TT>'q'</TT> but a confirmation request to exit must be
  answered as yes.
  </DD>
  </DL>
  <P>
  All keystrokes but ?,/,e,f, and q force another iteration which will
  reject additional pixels. To fully inhibit pixel rejection, the sigmas
  should be set to a large value (e.g. 100).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The following example will accumulate 8 spectra and fit the first
  aperture data interactively but not the second, and apply coincidence
  corrections to the sums. The upper and lower rejection criteria
  have been altered to bias the seventh order fit to a higher level.
  <P>
  	cl&gt; flatfit nite1 1-4,201-204 coin+ low=1.4 up=3 order=7
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  For some reason, the error plot is supposed to have a zero level line
  drawn, but none appears.
  <P>
  As in most of the IRAF software, the order of a fit refers to the number
  of terms in the fit, so that a fit of order 1 implies a constant and order
  2 implies a linear fit.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  coincor, flatdiv
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>