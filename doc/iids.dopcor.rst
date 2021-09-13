dopcor — Doppler correct spectra
================================

**Package: iids**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>dopcor (Jun94)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>dopcor (Jun94)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>dopcor</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  dopcor -- Apply doppler correction
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  dopcor input output redshift
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input spectra to be doppler corrected.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>List of doppler corrected spectra.  If no output list is specified then
  the input spectra are modified.  Also the output name may be
  the same as the input name to replace the input spectra by the
  calibrated spectra.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_redshift">redshift</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='redshift' Line='redshift'>
  <DD>Redshift or radial velocity (km/s) to be removed?  The spectra are corrected so
  that the specified redshift is removed; i.e. spectra with a positive
  velocity are shifted to shorter wavelengths and vice-versa.  This parameter
  may be either a number or an image header keyword with the desired redshift
  or velocity value.  An image header keyword may also have an initial minus
  sign, <TT>'-'</TT>, to specify the negative of a velocity or the redshift complement
  (1/(1+z)-1) of a redshift.  The choice between a redshift and a velocity is
  made with the <I>isvelocity</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_isvelocity">isvelocity = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='isvelocity' Line='isvelocity = no'>
  <DD>Is the value specified by the <I>redshift</I> parameter a velocity?  If
  no then the value is interpreted as a redshift and if it is yes then
  it is interpreted as a physical  velocity in kilometers per second.  Note that
  this is a relativistic velocity and not c*z!  For nearby cosmological
  velocities users should specify a redshift (z = v_cosmological / c).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_add">add = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='add' Line='add = no'>
  <DD>Add doppler correction to existing correction in "<TT>multispec</TT>" spectra?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_dispersion">dispersion = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dispersion' Line='dispersion = yes'>
  <DD>Apply a correction to the dispersion function?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_flux">flux = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='flux' Line='flux = no'>
  <DD>Apply a flux correction?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_factor">factor = 3</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='factor' Line='factor = 3'>
  <DD>Flux correction factor as a power of 1+z when applying a flux correction.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to be corrected.  If none are specified then all apertures
  are corrected.  An aperture list consists of comma separated aperture
  number or aperture number ranges.  A range is hypen separated and may
  include an interval step following the character <TT>'x'</TT>.  See <B>ranges</B>
  for further information.  For N-dimensional spatial spectra such as
  long slit and Fabry-Perot spectra this parameter is ignored.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print corrections performed?  The information includes the output image
  name, the apertures, the redshift, and the flux correction factor.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The input spectra (as specified by the input image list and apertures) are
  corrected by removing a specified doppler shift and written to the
  specified output images.  The correction is such that if the actual
  shift of the observed object is specified then the corrected spectra
  will be the rest spectra.  The opposite sign for a velocity or the
  redshift complement (1/(1+z)-1) may be used to add a doppler shift
  to a spectrum.
  <P>
  There are two common usages.  One is to take spectra with high doppler
  velocities, such as cosmological sources, and correct them to rest with
  respect to the earth.  In this case the measured redshift or velocity is
  specified to "<TT>remove</TT>" this component.  The other usage is to correct
  spectra to heliocentric or local standard of rest.  The heliocentric or LSR
  velocities can be computed and entered in the image header with the task
  <B>rvcorrect</B>.  In this case it is tempting to again think you are
  "<TT>removing</TT>" the velocity so that you specify the velocity as given in the
  header.  But actually what is needed is to "<TT>add</TT>" the computed standard of
  rest velocity to the observed spectrum taken with respect to the telescope
  to place the dispersion in the desired center of rest.  Thus, in this case
  you specify the opposite of the computed heliocentric or LSR velocity; i.e.
  use a negative.
  <P>
  The redshift or space velocity in km/s is specified either as a number or
  as an image header keyword containing the velocity or redshift.  If a
  number is given it applies to all the input spectra while an image header
  keyword may differ for each image.  The latter method of specifying a
  velocity is useful if velocity corrections are recorded in the image
  header.  See <B>rvcorrect</B> for example.
  <P>
  The choice between a redshift and a space velocity for the <I>redshift</I>
  parameter is made using the <I>isvelocity</I> parameter. If isvelocity=yes
  then the header dispersion solution is modified according to the
  relativistic Doppler correction:
  <P>
  	lambda_new = lamda_old * sqrt((1 + v/c)/(1 - v/c))
  <P>
  where v is the value of "<TT>redshift</TT>".  If isvelocity=no, <I>redshift</I> is
  interpreted as a cosmological redshift and the header dispersion solution
  is modified to give:
  <P>
  	lambda_new = lamda_old * z
  <P>
  where z is the value of "<TT>redshift</TT>"
  <P>
  If the <I>add</I> parameter is used and the image uses a "<TT>multispec</TT>"
  format where the previous doppler factor is stored separately
  then the new doppler factor is:
  <P>
  	znew = (1 + z) * (1 + zold) - 1 = z + zold + z * zold
  <P>
  where z is the specified doppler factor, zold is the previous one,
  and znew is the final doppler factor.  If the <I>add</I> parameter
  is no then the previous correction is replaced by the new correction.
  Note that for images using a linear or equispec coordinate system
  the corrections are always additive since a record is not kept of
  the previous correction.  Also any flux correction is made based
  on the specified doppler correction rather than znew.
  <P>
  There are two corrections which may be made and the user selects one
  or both of these.  A correction to the dispersion function is selected
  with the <I>dispersion</I> parameter.  This correction is a term to be
  applied to the dispersion coordinates defined for the image.  <I>The spectrum
  is not resampled, only the dispersion coordinate function is affected</I>.
  A correction to the flux, pixel values, is selected with the <I>flux</I>
  parameter.  This correction is only significant for cosmological redshifts.
  As such the correction is dependent on a cosmological model as well as
  whether a total flux or surface brightness is measured.  To provide the
  range of possible corrections the flux correction factor is defined by
  the <I>factor</I> parameter as the power of 1+z (where z is the
  redshift) to be multiplied into the observed pixel values.
  <P>
  A keyword DOPCORnn is added to the image header.  The index starts from
  01 and increments if multiple corrections are applied.  The value of
  the keywords gives the redshift applied, the flux factor if used, and
  the apertures which were corrected.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  To dispersion and flux correct a quasar spectrum with redshift of
  3.2 to a rest frame:
  <P>
  <PRE>
  	cl&gt; dopcor qso001.ms qso001rest.ms 3.2 flux+
  </PRE>
  <P>
  2.  To correct a set of spectra (in place) to heliocentric rest the task
  <B>rvcorrect</B> is used to set the VHELIO keyword using an observed
  velocity of 0.  Then:
  <P>
  <PRE>
  	cl&gt; dopcor *.imh "" -vhelio isvel+
  </PRE>
  <P>
  3.  To artificially add a redshift of 3.2 to a spectrum the complementary
  redshift is computed:
  <P>
  <PRE>
  	cl&gt; = 1/(1+3.2)-1
  	-0.76190476190476
  	cl&gt; dopcor artspec "" -0.762 flux+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_DOPCOR">DOPCOR V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='DOPCOR' Line='DOPCOR V2.10.3'>
  <DD>This task was extended to work on two and three dimensional spatial spectra
  such as long slit and Fabry-Perot spectra.
  <P>
  The <I>add</I> parameter was added.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_DOPCOR">DOPCOR V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='DOPCOR' Line='DOPCOR V2.10.3'>
  <DD>A keyword is added to log the correction applied.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_DOPCOR">DOPCOR V2.10.2</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='DOPCOR' Line='DOPCOR V2.10.2'>
  <DD>A sign error in converting velocity to redshift was fixed.  A validity
  check on the velocities and redshifts was added.  The documentation
  was corrected and improved.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_DOPCOR">DOPCOR V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='DOPCOR' Line='DOPCOR V2.10'>
  <DD>This task is new.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  ranges, rvcorrect
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>