ecreidentify — Automatically identify features in spectra
=========================================================

**Package: echelle**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>ecreidentify (Jun88)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.echelle</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>ecreidentify (Jun88)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>ecreidentify</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  ecreidentify -- Reidentify features in echelle spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  ecreidentify images reference
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Echelle images in which the features in the reference image are to be
  reidentified and a new dispersion function fit.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_reference">reference</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='reference' Line='reference'>
  <DD>Echelle image with previously identified features and dispersion
  function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_shift">shift = 0.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='shift' Line='shift = 0.'>
  <DD>Shift in user coordinates to be added to the reference features before
  centering.  If INDEF then a shift is determined by correlating the
  reference features to features automatically identified in the image to
  be reidentified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_cradius">cradius = 5.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='cradius' Line='cradius = 5.'>
  <DD>Centering radius in pixels.  If a reidentified feature falls further
  than this distance from the reference position (after shifting) it is
  not reidentified.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_threshold">threshold = 10.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='threshold' Line='threshold = 10.'>
  <DD>In order for a feature center to be determined the range of pixel
  intensities around the feature must exceed this threshold.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_refit">refit = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refit' Line='refit = yes'>
  <DD>Refit the dispersion function?  If yes and there are more than 4
  features in more than one order and a dispersion function was defined
  in the reference image then a new dispersion function of the same type
  and order offset
  as in the reference image is fit using the new pixel positions.
  Otherwise only a zero point shift is determined from the revised fitted
  coordinates without changing the form of the dispersion function.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_database">database = "<TT>database</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database = "database"'>
  <DD>Database containing the feature data for the reference image and in
  which the features for the reidentified images are recorded.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfiles">logfiles = "<TT>STDOUT,logfile</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfiles' Line='logfiles = "STDOUT,logfile"'>
  <DD>List of file in which to keep a processing log.  If a null file, "<TT></TT>", is
  given then no log is kept.  If the log file is "<TT>STDOUT</TT>" then the log is
  written to the terminal.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Emission or absorption features in a reference echelle spectrum are
  reidentified in other echelle spectra.  The features for the reference
  image and those determined for reidentified images are recorded in the
  specified database.
  <P>
  The first step in transferring identifications from the reference
  spectrum to another spectrum is to add a shift (in wavelength) to each
  feature in the reference image.  The shift is specified by the
  parameter <I>shift</I>.  This shift is for the fundamental order (order
  number 1) which is then applied to each order by dividing by the order
  number.  If the shift is specified as INDEF then a shift is determined
  by finding the peaks in the input spectrum and correlating these peaks
  against the feature in the reference spectrum.  This is the <TT>'x'</TT>
  algorithm described in <B>ecidentify</B>.
  <P>
  After the shift has been added to move the reference features to near
  the input spectrum features these positions are adjusted by centering
  on the features using the <B>center1d</B> algorithm.  The parameters
  <I>cradius</I> and <I>threshold</I> are used in this operation.  If the
  centering fails to find the feature within the centering radius
  (<I>cradius</I>) that feature is eliminated from the feature list.
  <P>
  If the parameter <I>refit</I> has the value "<TT>no</TT>" then the average shift
  in the feature positions is recorded as a zero point wavelength offset
  for the fundamental order without changing the shape of the dispersion
  function.  If the parameter has the value "<TT>yes</TT>" then the new feature
  positions are used to refit the dispersion function (of the same function
  type and orders).  The order offset is also maintained.
  <P>
  Log information is written to the specified log files.  To log this to
  the terminal, called the standard output, use STDOUT.  The log
  information includes reference spectrum, the spectrum being reidentified,
  the number of initial features and the number actually reidentified,
  the average shift in pixels, the average shift in wavelength (in terms
  of the fundamental order), the average fractional shift in wavelength
  (which can be scaled to a radial velocity), and the RMS of the features
  wavelengths given by the dispersion function to the user specified true
  wavelengths.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  The features in the spectrum f033.ec were identified previously
  with the task <B>ecidentify</B>.  The features positions in f043.ec are
  are reidentified with and without refitting the dispersion function as
  follows:
  <P>
  <PRE>
  ec&gt; ecreidentify f043.ec f033.ec
  <P>
  ECREIDENTIFY: NOAO/IRAF V2.7 seaman@puppis Mon 09:03:51 27-Jun-88
    Reference image = f033.ec, Refit = yes
                 Image    Found  Pix Shift  User Shift  Z Shift      RMS
               f043.ec  561/561       0.11       -1.07  -1.9E-6   0.0117
  <P>
  <P>
  ec&gt; ecreidentify f043.ec f033.ec refit=no
  <P>
  ECREIDENTIFY: NOAO/IRAF V2.7 seaman@puppis Mon 09:15:21 27-Jun-88
    Reference image = f033.ec, Refit = no
                 Image    Found  Pix Shift  User Shift  Z Shift      RMS
               f043.ec  561/561       0.11       -1.07  -1.9E-6   0.0131
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  center1d, ecidentify
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>