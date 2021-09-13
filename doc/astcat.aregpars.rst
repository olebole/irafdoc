.. _aregpars:

aregpars — Default region parameter set
=======================================

**Package: astcat**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  aregpars -- edit the region extraction parameters
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  aregpars
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>rcra = "<TT>00:00:00.0</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rcra' Line='rcra = "00:00:00.0"'>
  <DD>The right ascension / longitude of the center of the region to be extracted.
  </DD>
  </DL>
  <DL>
  <DT><B>rcdec = "<TT>+00:00.00</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rcdec' Line='rcdec = "+00:00.00"'>
  <DD>The declination / latitude of the center of the region to be extracted.
  </DD>
  </DL>
  <DL>
  <DT><B>rrawidth = 10.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rrawidth' Line='rrawidth = 10.0'>
  <DD>The right ascension / longitude width in minutes of arc of the region to
  be extracted.
  </DD>
  </DL>
  <DL>
  <DT><B>rdecwidth = 10.0</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rdecwidth' Line='rdecwidth = 10.0'>
  <DD>The declination / latitude width in minutes of arc of the region to
  be extracted.
  </DD>
  </DL>
  <DL>
  <DT><B>rcsystem = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rcsystem' Line='rcsystem = ""'>
  <DD>The input celestial coordinate system. This is the celestial coordinate system
  of the region center. If the input celestial coordinate system is undefined it
  defaults to the query celestial coordinate system. Popular options are
  "<TT>icrs</TT>", "<TT>j2000.0</TT>", and "<TT>b1950.0</TT>". The full set of options can be examined
  by typing "<TT>help ccsystems</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>rcraunits = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rcraunits' Line='rcraunits = ""'>
  <DD>The units of rcra. Permitted values are "<TT>hours</TT>", "<TT>degrees</TT>", and radians. If
  rcraunits is undefined it defaults to the preferred units of the
  input celestial coordinate system, e.g. hours for equatorial coordinate
  system, degrees for ecliptic, galactic, and super-galactic coordinate
  systems.
  </DD>
  </DL>
  <DL>
  <DT><B>rcdecunits = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rcdecunits' Line='rcdecunits = ""'>
  <DD>The units of rcdec. Permitted values are "<TT>degrees</TT>" and "<TT>radians</TT>". If rcdecunits
  is undefined it defaults to the preferred units of the input celestial
  coordinate system, e.g. degrees for all systems.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The region to extracted from the selected astrometric catalog or image survey
  is defined by the aregpars parameters <I>rcra</I>, <I>rcdec</I>, <I>rcrawidth</I>,
  and <I>rcdecwidth</I>.
  <P>
  <I>rcra</I> and <I>rcdec</I> are defined in the input celestial coordinate system
  specified by <I>rcsystem</I>.  If <I>rcsystem</I> is undefined it defaults to the
  query celestial coordinate system defined by the qsystem query parameter in
  the catalog configuration file.
  <P>
  <I>rcra</I> and <I>rcdec</I> are expressed in the units specified by 
  <I>rcraunits</I>, and <I>rcdecunits</I>.  If undefined <I>rcraunits</I> and
  <I>rcdecunits</I> are expressed in the preferred units of the input
  celestial coordinate system, e.g. hours and degrees for equatorial coordinate
  systems, and degrees and degrees for ecliptic, galactic,
  and super-galactic coordinate systems.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the region extraction parameters.
  <P>
  <PRE>
  cl&gt; lpar aregpars
  </PRE>
  <P>
  2. Edit the region extraction parameters.
  <P>
  <PRE>
  cl&gt; aregpars
  </PRE>
  <P>
  3. Edit the region extraction parameters from the agetcat task.
  <P>
  <PRE>
  cl&gt; epar agetcat
  </PRE>
  <P>
  4. Save the current aregpars parameter values in a text file called
  areg1.par.  Use the saved parameter set in the next call to the agetcat 
  task.
  <P>
  <PRE>
  cl&gt; epar aregpars
  cl&gt; agetcat ... aregpars=areg1.par ...
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  agetcat, agetim, help ccsystems
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
