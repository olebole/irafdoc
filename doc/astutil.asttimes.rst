asttimes — Compute UT, Julian day, epoch, and sidereal time
===========================================================

**Package: astutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>asttimes (May93)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>astutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>asttimes (May93)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>asttimes</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  asttimes -- Compute UT, Julian day, epoch, and sidereal time
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  asttimes
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_files">files = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files = ""'>
  <DD>List of files containing local dates and times for which the astronomical
  dates and times are desired.  If no input files are specified then task
  parameters are used.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_header">header = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='header' Line='header = yes'>
  <DD>Print header and observatory information to output?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_observatory">observatory = "<TT>)_.observatory</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = ")_.observatory"'>
  <DD>Observatory for  which times are to be computed.  The default is a
  redirection to look in the parameters for the parent package for a value.
  The final value of this parameter may be one of the
  observatories in the observatory database, "<TT>observatory</TT>" to select the
  observatory defined by the environment variable "<TT>observatory</TT>" or the
  parameter <B>observatory.observatory</B>, or "<TT>obspars</TT>" to select the
  current parameters set in the <B>observatory</B> task.  See help for
  <B>observatory</B> for additional information.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_year">year, month, day, time</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='year' Line='year, month, day, time'>
  <DD>If no input files are specified then the date and time for which the
  astronomical date and time is computed are given by these parameters.
  If the year is less than 100 then the century is assumed to be 1900.
  The month is specified as an integer between 1 and 12, and the local
  time for the specified time zone is in hours (sexagesimal format is
  acceptable).
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ut">ut, epoch, jd, lmst</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ut' Line='ut, epoch, jd, lmst'>
  <DD>If no input files are specified then the universal time, J2000 Julian epoch,
  Julian day, and local mean sidereal time (at the specified longitude)
  are recorded in these parameters for possible reference as CL
  variables.  This is in addition to the usual printed output.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The astronomical quantities of universal time, J2000 Julian epoch, Julian day,
  and local mean sidereal time at the specified observatory are computed and
  printed for the given dates and times.  To compute parameters for a
  location not specified in the observatory database use the observatory name
  "<TT>obspars</TT>" which will use the values defined by the parameters
  <I>observatory.longitude</I> and <I>observatory.timezone</I>.  The input
  dates and times may be taken from files containing the year, month (as an
  integer between 1 and 12), day, and local time (sexagesimal notation is
  acceptable) in the specified time zone.  If no files are specified then task
  parameters are used.  The output consists of a printed table with optional
  header and the input data and derived astronomical data.  In addition, if
  the input date and time is from the task parameters then the astronomical
  times are recorded in the user's parameter file (provided the task is not
  run as a background job).  These parameters may then be used as CL
  parameters.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. For use directly without data files set the date and time using
  the parameter editor, with explicit assignments, or on the command line:
  <P>
  <PRE>
      cl&gt; asttimes year=1987 month=10 day=28 time=15:30 obs=kpno
      # ASTTIMES: Observatory parameters for Kitt Peak National Observatory
      #       timezone = 7
      #       longitude = 111:36.0
      ##YR MON   DAY          ZT         UT      EPOCH           JD       LMST
      1987  10 28 WED 15:30:00.0 22:30:00.0 1987.82324 2447097.4375 17:30:31.8
      cl&gt; =asttimes.lmst
      17.508823973881
  </PRE>
  <P>
  2. To make a table using a CL loop:
  <P>
  <PRE>
      cl&gt; asttimes.observatory="kpno"
      cl&gt; asttimes.year=1987
      cl&gt; asttimes.month=10
      cl&gt; asttimes.time=0
      cl&gt; for (i=10; i&lt;16; i+=1) {
      &gt;&gt;&gt; asttimes (day=i, header=no)
      &gt;&gt;&gt; }
      1987  10 10 SAT  0:00:00.0  7:00:00.0 1987.77219 2447078.7917  0:47:01.0
      1987  10 11 SUN  0:00:00.0  7:00:00.0 1987.77493 2447079.7917  0:50:57.5
      1987  10 12 MON  0:00:00.0  7:00:00.0 1987.77766 2447080.7917  0:54:54.1
      1987  10 13 TUE  0:00:00.0  7:00:00.0 1987.78040 2447081.7917  0:58:50.7
      1987  10 14 WED  0:00:00.0  7:00:00.0 1987.78314 2447082.7917  1:02:47.2
      1987  10 15 THU  0:00:00.0  7:00:00.0 1987.78588 2447083.7917  1:06:43.8
  </PRE>
  <P>
  In practice the output would be directed to a file:
  <P>
      &gt;&gt;&gt; asttimes (day=i, header=no, &gt;&gt;"<TT>table</TT>")
  <P>
  3. To use an input file:
  <P>
  <PRE>
      cl&gt; asttimes f=dates &gt; table
      cl&gt; type table
      # ASTTIMES: Observatory parameters for Kitt Peak National Observatory
      #       timezone = 7
      #       longitude = 111:36.0
      ##YR MON   DAY          ZT         UT      EPOCH           JD       LMST
      1987  10 28 WED 22:00:00.0  5:00:00.0 1987.82398 2447097.7083  0:01:35.8
      1987  10 28 WED 23:00:00.0  6:00:00.0 1987.82409 2447097.7500  1:01:45.7
      1987  10 29 THU  0:00:00.0  7:00:00.0 1987.82421 2447097.7917  2:01:55.5
      1987  10 29 THU  1:00:00.0  8:00:00.0 1987.82432 2447097.8333  3:02:05.4
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_revisions">REVISIONS</A></H2>
  <! BeginSection: 'REVISIONS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_ASTTIMES">ASTTIMES V2.10.3</A></B></DT>
  <! Sec='REVISIONS' Level=0 Label='ASTTIMES' Line='ASTTIMES V2.10.3'>
  <DD>The epoch was changed from day of the year divided by 365.25 to the
  precise J2000 Julian epoch definition.  In addition to changing
  the output value this fixes incorrect values JD and LMST around the
  new year.
  <P>
  The times are now always printed in the proper 24 hour interval instead
  of using negative or values greater than 24 to indicate the day difference
  with Greenwich.
  <P>
  The header parameter now suppress printing the observatory information.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'REVISIONS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  observatory
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'REVISIONS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>