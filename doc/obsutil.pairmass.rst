.. _pairmass:

pairmass — Plot airmass vs time for a given coordinate
======================================================

**Package: obsutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  pairmass -- plot the airmass for a given object
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  pairmass
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>ra</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra' Line='ra'>
  <DD>The right ascension of the object in hours.
  </DD>
  </DL>
  <DL>
  <DT><B>dec</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dec' Line='dec'>
  <DD>The declination of the object in degrees.
  </DD>
  </DL>
  <DL>
  <DT><B>epoch=INDEF</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='epoch' Line='epoch=INDEF'>
  <DD>The epoch of the coordinates in years.
  </DD>
  </DL>
  <DL>
  <DT><B>year</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='year' Line='year'>
  <DD>The year of the observation.
  </DD>
  </DL>
  <DL>
  <DT><B>month</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='month' Line='month'>
  <DD>The month of the observation (a number from 1 to 12).
  </DD>
  </DL>
  <DL>
  <DT><B>day</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='day' Line='day'>
  <DD>The day of the month of the observation.
  </DD>
  </DL>
  <DL>
  <DT><B>observatory = "<TT>observatory</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observatory' Line='observatory = "observatory"'>
  <DD>The observatory identifier in the observatory database.  See the
  help for <B>observatory</B> task for more information.
  </DD>
  </DL>
  <DL>
  <DT><B>timesys = "<TT>Standard</TT>" (Universal|Standard|Siderial)</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='timesys' Line='timesys = "Standard" (Universal|Standard|Siderial)'>
  <DD>Time system for the plot or output list.  The choices are
  "<TT>Universal</TT>" for universal time, "<TT>Standard</TT>" for standard time (where
  the time zone is determined from the observatory database), and "<TT>Siderial</TT>"
  for the siderial time.
  </DD>
  </DL>
  <P>
  <DL>
  <DT><B>resolution=4</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='resolution' Line='resolution=4'>
  <DD>The number of UT points per hour for which to calculate the airmass.
  </DD>
  </DL>
  <DL>
  <DT><B>listout=no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='listout' Line='listout=no'>
  <DD>List, rather than plot, the airmass versus time?  Only airmasses
  below that given by the <I>wy2</I> parameters are listed.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Plot parameters</H3>
  <! BeginSection: 'PLOT PARAMETERS'>
  <UL>
  <DL>
  <DT><B>wx1=-7., wx2=7., wy1=0., wy2=5.</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='wx1' Line='wx1=-7., wx2=7., wy1=0., wy2=5.'>
  <DD>The range of window (user) coordinates to be included in the plot.
  If the range of values in x or y = 0, the plot is automatically
  scaled from the minimum to maximum data values along that axis.
  The times are available from -24 hours to 48 hours so one can use
  negative numbers to plot hours from midnight or in actual hours.
  </DD>
  </DL>
  <DL>
  <DT><B>pointmode = no</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='pointmode' Line='pointmode = no'>
  <DD>Plot individual points instead of a continuous line?
  </DD>
  </DL>
  <DL>
  <DT><B>marker="<TT>box</TT>"</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='marker' Line='marker="box"'>
  <DD>If <B>pointmode</B> = yes, the marker drawn at each point is set with this
  parameter.  The acceptable choices are "<TT>point</TT>", "<TT>box</TT>", "<TT>plus</TT>", "<TT>cross</TT>",
  "<TT>circle</TT>", "<TT>hebar</TT>", "<TT>vebar</TT>", "<TT>hline</TT>", "<TT>vline</TT>", and "<TT>diamond</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>szmarker = 0.005</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='szmarker' Line='szmarker = 0.005'>
  <DD>The size of the marker drawn when <B>pointmode</B> = yes.  A value of 0
  (zero) indicates that the task should read the size from the input list.
  </DD>
  </DL>
  <DL>
  <DT><B>logx = no, logy = no</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='logx' Line='logx = no, logy = no'>
  <DD>Draw the x or y axis in log units, versus linear?
  </DD>
  </DL>
  <DL>
  <DT><B>xlabel="<TT>default</TT>"</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='xlabel' Line='xlabel="default"'>
  <DD>Label for the X-axis.  The value "<TT>default</TT>" uses the specified time system.
  </DD>
  </DL>
  <DL>
  <DT><B>ylabel="<TT>Airmass</TT>"</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='ylabel' Line='ylabel="Airmass"'>
  <DD>Labels for the Y-axis.
  </DD>
  </DL>
  <DL>
  <DT><B>title="<TT>default</TT>"</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='title' Line='title="default"'>
  <DD>Title for plot.  If not changed from "<TT>default</TT>", a title string consisting
  of the date, observatory, and  object position is used.
  </DD>
  </DL>
  <DL>
  <DT><B>vx1=0., vx2=0., vy1=0., vy2=0.</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='vx1' Line='vx1=0., vx2=0., vy1=0., vy2=0.'>
  <DD>NDC coordinates (0-1) of the plotting device viewport.  If not set
  by the user, a suitable viewport which allows sufficient room for all
  labels is used.
  </DD>
  </DL>
  <DL>
  <DT><B>majrx=5, minrx=5, majry=5, minry=5</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='majrx' Line='majrx=5, minrx=5, majry=5, minry=5'>
  <DD>The number of major and minor divisions along the x or y axis.
  </DD>
  </DL>
  <DL>
  <DT><B>round = no</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='round' Line='round = no'>
  <DD>Round axes up to nice values?
  </DD>
  </DL>
  <DL>
  <DT><B>fill = yes</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='fill' Line='fill = yes'>
  <DD>Fill the plotting viewport regardless of the device aspect ratio?
  </DD>
  </DL>
  <DL>
  <DT><B>append = no</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>Append to an existing plot?
  </DD>
  </DL>
  <DL>
  <DT><B>device="<TT>stdgraph</TT>"</B></DT>
  <! Sec='PLOT PARAMETERS' Level=0 Label='device' Line='device="stdgraph"'>
  <DD>Output device.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PLOT PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The airmass is plotted over a specified set of hours for a given
  observatory.  The observatory is specified by an identifier as given
  in the observatory database.  See the help for "<TT>observatory</TT>" for more
  information about the database and identifiers.
  <P>
  The results can be shown in universal, standard, or siderial time.
  The standard time simply adds the time zone from the observatory
  database tothe universal time and so there is no explicit facility
  for daylight savings time.  The times are computed in the range
  -24 hours to +48 hours.  By setting the <I>wx1</I> and <I>wx2</I>
  parameters one can plot either in hours relative to 0 in the specified
  time system or as positive hours.  This simple task does not support
  axis labeling which wraps around.
  <P>
  The list output prints date, observatory, object coordinates, and
  the time system.  This is followed by the time sorted between 0 and 24
  and the airmasses.  The list only includes airmasses below the
  value specified by <I>wy2</I>.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  To plot the airmass for M82 from Kitt Peak for Groundhog's Day in 1992:
  <P>
  <PRE>
      pairmass ra=9:51:42 dec=69:56 epoch=1950 year=1992 month=2 day=2
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  observatory, airmass, setairmass, graph
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'PLOT PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
