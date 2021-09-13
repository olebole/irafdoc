.. _aslist:

aslist — List the supported image surveys
=========================================

**Package: astcat**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  aslist -- list the supported image surveys
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  aslist catalogs
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>imsurveys</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imsurveys' Line='imsurveys'>
  <DD>The names of the image surveys to be listed. If surveys = "<TT>*</TT>" then
  all the image surveys in the image survey configuration file are listed.
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>List the image survey wcs and keyword information  after the image survey
  name ?
  </DD>
  </DL>
  <DL>
  <DT><B>imdb = "<TT>)_.imdb</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imdb' Line='imdb = ")_.imdb"'>
  <DD>The image survey configuration file. The value of imdb defaults to the value
  of the package parameter of the same name. The default image survey
  configuration file is "<TT>astcat$lib/imdb.dat</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Aslist lists the supported image surveys specified by the
  <I>imsurveys</I> parameter. If imsurveys = "<TT>*</TT>" then all the supported image
  surveys are listed, otherwise only the image survey names specified by the
  user are listed. Valid image survey names have the form imsurvey@site, e.g.
  "<TT>dss1@cadc</TT>".  If <I>verbose</I> = "<TT>yes</TT>", then the image survey wcs and
  keyword information is listed after the image survey name.
  <P>
  The image survey names, addresses, query formats, output formats, wcs formats,
  and keyword formats, are specified in the image survey configuration file
  <I>imdb</I>. By default the image survey configuration file names defaults to
  the value of the imdb package parameters. The default image survey
  configuration file is "<TT>astcat$lib/imdb.dat</TT>".  Users can add records
  to this file or create their own configuration file.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List all the image surveys in the image survey configuration file.
  <P>
  <PRE>
  cl&gt; aslist *
  </PRE>
  <P>
  2. List the wcs and keyword information for the dss1@cadc image survey.
  <P>
  <PRE>
  cl&gt; aslist dss1@cadc verbose+
  </PRE>
  <P>
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
  aclist
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
