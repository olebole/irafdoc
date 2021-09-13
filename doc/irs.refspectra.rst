refspectra — Assign reference spectra to object spectra
=======================================================

**Package: irs**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>refspectra (Mar92)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.onedspec</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>refspectra (Mar92)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>refspectra</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  refspectra -- Assign reference spectra
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  refspectra input [records]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>List of input spectra or root names to be assigned reference spectra.
  When using the record number extension format, record number extensions
  will be appended to each root name in the list.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_records">records (imred.irs and imred.iids packages only)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='records' Line='records (imred.irs and imred.iids packages only)'>
  <DD>List of records or ranges of records to be appended to the input root
  names when using record number extension format.  The syntax of this
  list is comma separated record numbers or ranges of record numbers.  A
  range consists of two numbers separated by a hyphen. An example of this
  syntax is "<TT>1-5,13,17-19</TT>".  A null list ("<TT></TT>") may
  be used if no record number extensions are desired.  This is a
  positional query parameter only if the record format is specified with
  the <I>recformat</I> parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_references">references = "<TT>*.imh</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='references' Line='references = "*.imh"'>
  <DD>List of reference spectra to be assigned or a "<TT>reference spectra assignment
  table</TT>" (see DESCRIPTION section).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_apertures">apertures = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='apertures' Line='apertures = ""'>
  <DD>List of apertures to be SELECTED from the input list of spectra.  If no list
  is specified then all apertures are selected.  The syntax is the same as the
  record number extensions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_refaps">refaps = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='refaps' Line='refaps = ""'>
  <DD>List of reference spectra apertures to be SELECTED.  If no list is specified
  then all apertures are selected.  The syntax is the same as the record number
  extensions.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ignoreaps">ignoreaps = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ignoreaps' Line='ignoreaps = yes'>
  <DD>Ignore the input and reference apertures when ASSIGNING reference spectra.
  If the aperture numbers are not ignored then only the reference spectra with
  the same aperture number as a particular input spectra are used when assigning
  reference spectra.  Otherwise all the reference spectra are used.  This does
  not apply to the "<TT>match</TT>" and "<TT>average</TT>" options which always ignore the aperture
  numbers.  Note that this parameter applies to relating reference spectra to
  input spectra and does not override the aperture selections on the input
  spectra and reference spectra.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_select">select = "<TT>interp</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='select' Line='select = "interp"'>
  <DD>Selection method for assigning reference spectra.  The methods are:
  <DL>
  <DT><B><A NAME="l_average">average</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='average' Line='average'>
  <DD>Average two reference spectra without regard to any aperture,
  sort, or group parameters.
  If only one reference spectrum is specified then it is assigned with a
  warning.  If more than two reference spectra are specified then only the
  first two are used and a warning is given.  There is no checking of the
  aperture numbers or group values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_following">following</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='following' Line='following'>
  <DD>Select the nearest following spectrum in the reference list based on the
  sort and group parameters.  If there is no following spectrum use the
  nearest preceding spectrum.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_interp">interp</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='interp' Line='interp'>
  <DD>Interpolate between the preceding and following spectra in the reference
  list based on the sort and group parameters.  If there is no preceding and
  following spectrum use the nearest spectrum.  The interpolation is weighted
  by the relative distances of the sorting parameter (see cautions in
  DESCRIPTION section).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_match">match</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='match' Line='match'>
  <DD>Match each input spectrum with the reference spectrum list in order.
  This overrides any aperture or group values.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_nearest">nearest</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='nearest' Line='nearest'>
  <DD>Select the nearest spectrum in the reference list based on the sort and
  group parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_preceding">preceding</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='preceding' Line='preceding'>
  <DD>Select the nearest preceding spectrum in the reference list based on the
  sort and group parameters.  If there is no preceding spectrum use the
  nearest following spectrum.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_sort">sort = "<TT>jd</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='sort' Line='sort = "jd"'>
  <DD>Image header keyword to be used as the sorting parameter for selection
  based on order.  The header parameter must be numeric but otherwise may
  be anything.  Common sorting parameters are times or positions.
  A null string, "<TT></TT>", or the word "<TT>none</TT>" may be use to disable the sorting
  parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_group">group = "<TT>ljd</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='group' Line='group = "ljd"'>
  <DD>Image header keyword to be used to group spectra.  For those selection
  methods which use the group parameter the reference and object spectra must
  have identical values for this keyword.  This can be anything but it must
  be constant within a group.  Common grouping parameters are the date of
  observation "<TT>date-obs</TT>" (provided it does not change over a night) or the
  local Julian day number.  A null string, "<TT></TT>", or the word "<TT>none</TT>" may be use
  to disable the grouping parameter.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_time">time = no, timewrap = 17.</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='time' Line='time = no, timewrap = 17.'>
  <DD>Is the sorting parameter a 24 hour time?  If so then the time orgin
  for the sorting is specified by the timewrap parameter.  This time
  should precede the first observation and follow the last observation
  in a 24 hour cycle.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_override">override = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='override' Line='override = no'>
  <DD>Override previous assignments?  If an input spectrum has reference
  spectra assigned previously the assignment will not be changed unless
  this flag is set.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_confirm">confirm = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='confirm' Line='confirm = yes'>
  <DD>Confirm reference spectrum assignments?  If <I>yes</I> then the reference
  spectra assignments for each input spectrum are printed and the user may
  either accept the assignment or not.  Rejected assignments leave the
  input spectrum unchanged.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_assign">assign = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='assign' Line='assign = yes'>
  <DD>Assign the reference spectrum by entering it in the image header?
  The input spectra are only modified if this parameter is <I>yes</I>.
  This parameter may be set to <I>no</I> to get a list of assignments
  without actually entering the assignments in the image headers.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_logfiles">logfiles = "<TT>STDOUT,logfile</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='logfiles' Line='logfiles = "STDOUT,logfile"'>
  <DD>List of log files for recording reference spectra assignments.
  The file STDOUT prints to the standard output.  If not specified ("<TT></TT>")
  then no logs will be recorded.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Verbose log output?  This prints additional information about the input
  and reference spectra.  This is useful for diagnosing why certain spectra
  are ignored or not assigned as intended.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  This task allows the user to define which reference spectra are to be 
  used in the calculation of the dispersion solution of object spectra.
  The assignment of reference spectra to object spectra is often
  a complex task because of the number of spectra, the use of many distinct
  apertures, and different modes of observing such as interspersed arc
  calibration spectra or just one calibration for a night.  This task
  provides a number of methods to cover many of the common cases.
  <P>
  A reference spectrum is defined to be a spectrum that has been used to
  calculate a wavelength solution with the tasks IDENTIFY or REIDENTIFY.
  These tasks have set the keyword REFSPEC1 in the image header
  equal to the spectrum's own name.
  <P>
  Wavelength reference spectra are assigned to input spectra by entering
  the reference spectrum name or pair of names in the image
  header under the keywords REFSPEC1 and REFSPEC2.  When two reference
  spectra are assigned, the spectrum names may be followed by a weighting
  factor (assumed to be 1 if missing).  The wavelength of a pixel is
  then the weighted average of the wavelengths from the reference
  spectra dispersion solutions.  The weighting factors are calculated
  by choosing an appropriate selection method, ie average, interpolation,
  etc. Note, however, that these assignments may be made directly using
  the task <B>hedit</B> or with some other task or script if none of the
  methods are suitable. 
  <P>
  The spectra to be assigned references are specified by an input list.
  Optional numeric record format extensions may be appended to each name
  (used as a root name) in the input list in the <B>iids/irs</B> packages.
  The input spectra may be restricted to a particular set of aperture numbers
  by the parameter <I>apertures</I>; the spectra not in the list of apertures
  are skipped.  If the aperture list is null (i.e. specified as "<TT></TT>") then all
  apertures are selected.  One further selection may be made on the input
  spectra.  If the parameter <I>override</I> is no then input spectra which
  have existing reference spectra assignments (which includes the reference
  spectra) are skipped.
  <P>
  The reference spectra parameter <I>references</I> may take two forms.
  It may be an image list of spectra or a text file containing
  a "<TT>reference spectrum assignment table</TT>".  The table consists of pairs
  of strings/lists with the first string being a list of object spectra
  and the second string being a list of reference spectra.  If this
  table is used, then only those object spectra in the table that are also
  listed in the input parameter list are processed.  The example below
  illustrates the reference spectrum assignment table:
  <P>
  <PRE>
  	spec1		spec2,spec3,spec4
  	spec5
  	spec6,spec7	spect8,spec9
  	spec10		spec11
  	spec12		spec13
  	spec14		spec15
  </PRE>
  <P>
  As a convenience, if a reference list in the table is missing, the preceding
  reference list is implied. This table may be used to make arbitrary assignments.
  <P>
  The reference spectra in the specified list may also be restricted to a
  subset of aperture numbers.  However, in the case of averaging, the
  reference aperture selection is ignored. In the case of matching, if
  a reference spectrum is not selected then the matching input spectrum
  is also skipped (in order to maintain a one-to-one correspondence).
  Spectra in the reference list which are not reference spectra (as
  defined earlier) are also ignored and a warning is printed.  Note that
  no check is made that a dispersion solution actually exists in the
  dispersion solution database.
  <P>
  There may be cases where there are only reference spectra for some
  apertures and it is desired to apply these reference spectra to the
  other apertures.  The <I>ignoreaps</I> flag may be used to force an
  assignment between reference and object spectra with different
  aperture numbers.  Note that this flag is applied after the input and
  reference list aperture number selections are made; in other words this
  applies only to the assignments and not the input selection process.
  <P>
  Once the appropriate reference spectra from the reference list have been
  determined for an input spectrum they are assigned using one of the
  methods selected by the parameter <I>select</I>.  The "<TT>match</TT>" method
  simply pairs each element of the input spectrum list with each element
  in the reference spectrum list.  If a reference assignment table
  is used with "<TT>match</TT>", then only the first spectrum in the reference
  list for each input spectrum is assigned.
  <P>
  The "<TT>average</TT>" method assigns the first two spectra in the reference list
  ignoring aperture numbers or groups. The spectra are averaged by assigning
  equal weights.  There is no weighting based on any sort parameter.  If
  there are more than two spectra in the reference list then only the first
  two spectra are used and the remainder are ignored.  If a reference
  assignment table is used only the first two reference spectra listed for
  each object in the table are averaged.
  <P>
  The remaining selection methods group the spectra using a header keyword
  which must be constant within a group.  If no group parameter is specfied
  (the null string "<TT></TT>" or the word "<TT>none</TT>")
  then grouping does not occur.  Only reference spectra with the same
  group header value as the object are assigned to an object spectrum.
  One likely group parameter is the "<TT>date-obs</TT>" keyword.  This is usually
  constant over a night at CTIO and KPNO.  At other sites this may not
  be the case.  Therefore, the task <B>setjd</B> may be used to set a
  local Julian day number which is constant over a night at any
  observatory.
  <P>
  Within a group the spectra are ordered based on a numeric image header
  parameter specified by the <I>sort</I> parameter.  A null string "<TT></TT>" or the
  word "<TT>null</TT>" may be used to select no sort parameter.  Parameters which are
  times, as indicated by the <I>time</I> parameter, are assumed to be cyclic
  with a period of 24 hours.  The time wrap parameter defines the origin of a
  cycle and should precede the first observation and follow the last
  observation in a 24 hour period; i.e. for nighttime observations this
  parameter value should bee sometime during the day.  Particularly with
  interpolating or choosing the nearest reference spectrum it is important
  that the sorting parameter refer to the middle of the exposure.  A Julian
  date at the middle of an exposure may be calculated with the task
  <B>setjd</B> or a middle UT time may be computed with the task
  <B>setairmass</B>.
  <P>
  The selection methods may choose the "<TT>nearest</TT>", "<TT>preceding</TT>", or "<TT>following</TT>"
  reference spectrum.  Alternatively, the reference wavelengths may be
  interpolated between the preceding and following reference spectra with
  weights given by the relative distances measured by the sorting parameter.
  In the cases where a preceding or following spectrum is required and one is
  not found then the nearest reference spectrum is used.  These methods are
  used for observing sequences where the reference spectra are taken either
  nearby in time or space.
  <P>
  The option "<TT>interp</TT>" should not be used without some thought as to the
  nature of the interpolation.  If the sorting parameter is a time (a 24 hour
  cyclic parameter as opposed to a continuous parameter such as a Julian
  date) then the user must be aware of when these times were recorded in the
  header.  For example, let us assume that the sort parameter is "<TT>ut</TT>" and
  that this time was recorded in the header at the beginning of the
  exposure.  If the object spectrum exposure time is longer than the
  reference spectra exposure times, then interpolation will weight the
  preceding reference spectrum too heavily.  This problem can be circumvented
  by using the "<TT>average</TT>" selection method along with the reference assignment
  table.  Or the sort time parameter in the headers of the spectra can be
  changes with <I>setjd</I> or <I>setairmass</I> or edited to reflect the
  values at mid-exposure (see EXAMPLES).
  <P>
  Once the reference spectrum or spectra for a input spectrum have been 
  identified the user may also chose to override any previous reference
  assignments, to accept or not accept the current reference assignments
  (in the case of not accepting the reference assignment the image header
  is not updated), to only list the current reference assignments and not
  update any image headers, as well as to record the reference assignments
  to log files.  These options are separately controlled by the remaining
  task parameters. 
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_keywords">KEYWORDS</A></H2>
  <! BeginSection: 'KEYWORDS'>
  <UL>
  This task uses the header keyword BEAM-NUM to sort the apertures.  It
  has an integer value.  If the keyword does not exist then all apertures
  are assumed to be 1.
  <P>
  The keyword REFSPEC1 is used to search for reference spectra. This 
  keyword can be previously created by the tasks IDENTIFY and REIDENTIFY.
  <P>
  The two keywords REFSPEC1 and optionally REFSPEC2 are created by the
  task when the assign parameter is set to yes.  They take the form:
  <P>
  <PRE>
             REFSPEC1='d1.0001'  or
  <P>
             REFSPEC1='d5.0001 0.756'
             REFSPEC2='d5.0002 0.244'
  </PRE>
  <P>
  </UL>
  <! EndSection:   'KEYWORDS'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  Compute a Julian date at the midpoint of the exposure for sorting
  and a local Julian day number for grouping and then assign spectra
  using interpolation.
  <P>
  <PRE>
      cl&gt; setjd *.imh jd=jd ljd=ljd
      cl&gt; refspec *.imh sort=jd group=ljd select=interp
  </PRE>
  <P>
  2.  Specifically assign reference spectra to input spectra.
  <P>
  <PRE>
      cl&gt; refspectra spec1,spec3 refe=spec2,spec4 select=match
  </PRE>
  <P>
  3.  Use a reference assignment table to assign reference spectra to input
  spectra using the "<TT>average</TT>" option.  First a table is created using an
  editor.
  <P>
  <PRE>
      cl&gt; type reftable
      spec1		spec2,spec3,spec4
      spec5
      spec6,spec7		spect8,spec9
      spec10		spec11
      spec12		spec13
      spec14		spec15
      cl&gt; refspec spec*.imh recfor- select=average refe=reftable
  </PRE>
  <P>
  4.  Assign the nearest reference spectrum in zenith distance using
  wildcard lists.  By default the aperture numbers must match.
  <P>
      cl&gt; refspec *.imh "<TT></TT>" sort=zd select=nearest time-
  <P>
  5.  Assign a specific reference spectrum to all apertures.
  <P>
      cl&gt; refspec *.imh "<TT></TT>" refer=refnite1 ignoreaps+
  <P>
  6.  Confirm assignments.
  <P>
  <PRE>
      cl&gt; hselect irs.*.imh "$I,beam-num,ut,refspec1" yes
      irs.0009.imh	0	0:22:55		irs.0009
      irs.0010.imh	1	0:22:53		irs.0010
      irs.0100.imh	0	8:22:55
      irs.0101.imh	1	8:22:53
      irs.0447.imh	0	13:00:07	irs.0447
      irs.0448.imh	1	13:00:05	irs.0448
      cl&gt; refspec irs 100-101 refer=irs.*.imh conf+ ver+ select=nearest\<BR>
         &gt;&gt;&gt; ignoreaps-
      [irs.0100] Not a reference spectrum
      [irs.0101] Not a reference spectrum
      [irs.0100] refspec1='irs.0447'   Accept assignment (yes)?
      [irs.0101] refspec1='irs.0448'   Accept assignment (yes)?
  </PRE>
  <P>
  Because the reference spectrum list includes all spectra the
  warning messages "<TT>Not a reference spectrum</TT>" are printed with verbose
  output.  Remember a reference spectrum is any spectrum which has a
  reference spectrum assigned which refers to itself.
  <P>
  7.  Assign reference spectra with weights using interpolation.  In this
  example we want to sort by "<TT>ut</TT>" but this keyword value was 
  recorded at the beginning of the integration. So we first create an
  new keyword and then compute its value to be that of mid-exposure.  The
  new keyword is then used as the sorting parameter.
  <P>
  <PRE>
      cl&gt; hedit *.imh utmid 0. add+ ver- show-     
      cl&gt; hedit *.imh utmid "(ut)" ver- show-
      cl&gt; hedit *.imh utmid "(mod(utmid+exptime/7200.,24.))" ver- show-
      cl&gt; refspec *.imh refer=*.imh recfor- select=interp sort=utmid
  </PRE>
  <P>
  8.  Assign reference spectra using the "<TT>average</TT>" option and the reference
  assignment table with data with record number extensions.  First edit
  the file reftable:
  <P>
  <PRE>
       cl&gt; type reftable
              spec.0001     arc1.0001,arc2.0001
              spec.0002     arc1.0002,arc2.0002
              spec.0003     arc1.0003,arc2.0003
              spec.0004     arc1.0004,arc2.0004
       cl&gt; refspec spec.*.imh recfor- refer=reftable select=average
  </PRE>
  <P>
  9.  Assign a reference spectrum for aperture 1 to the object spectra
  for apertures 2 thru 5.
  <P>
  <PRE>
       cl&gt; refspec spec 2-5 recfor+ refer=arc.*.imh refaps=1 ignoreaps+
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_REFSPECTRA">REFSPECTRA V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='REFSPECTRA' Line='REFSPECTRA V2.10.3'>
  <DD>If no reference spectrum is found in the interp, nearest, following,
  preceding methods then a list of the reference spectra is given
  showing why each was not acceptable.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_REFSPECTRA">REFSPECTRA V2.10</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='REFSPECTRA' Line='REFSPECTRA V2.10'>
  <DD>A group parameter was added to allow restricting assignments by observing
  period; for example by night.  The record format option was removed and
  the record format syntax is available in the <B>irs/iids</B> packages.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  identify, reidentify, dispcor, setjd, setairmass
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'KEYWORDS' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>