.. _adumpcat:

adumpcat — Catalog access debugging task
========================================

**Package: astcat**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  adumpcat -- query a catalog and capture the results
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  adumpcat catalog output ra dec size
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>catalog</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catalog' Line='catalog'>
  <DD>The name of the catalog to be queried. Catalog names have the form
  catalog@site, e.g. "<TT>usno2@noao</TT>". The catalog address and query format are
  stored in a record called catalog in  the catalog configuration file.
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>The name of the output query results file. The query results are written
  to the output file without modification, i.e. they may contain comments,
  HTML markup, etc as well as the object list.
  </DD>
  </DL>
  <DL>
  <DT><B>ra  </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ra' Line='ra  '>
  <DD>The right ascension of the field center in the units expected by the catalog
  query. The value of ra replaces the default value of the ra query parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>dec  </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='dec' Line='dec  '>
  <DD>The declination of the field center in the units expected by the catalog query.
  The value of dec replaces the default value of the dec query parameters.
  It may be necessary to add or remove a leading + to make the query work
  correctly.
  </DD>
  </DL>
  <DL>
  <DT><B>size</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='size' Line='size'>
  <DD>The field size in units expected by the catalog query. The value of size
  replaces the default value of the width, ra/xwidth, dec/ywidth,
  hwidth, x/rahwidth, y/dechwidth, or radius query parameters as appropriate.
  </DD>
  </DL>
  <DL>
  <DT><B>catdb = "<TT>)_.catdb</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catdb' Line='catdb = ")_.catdb"'>
  <DD>The catalog configuration file. The name of the catalog configuration file
  defaults to the value of the package parameter of the same name.  The
  default configuration file is "<TT>astcat$lib/catdb.dat</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Adumpcat is a simple catalog access debugging task which queries the
  astrometric catalog <I>catalog</I>, captures the results, and writes them
  to the file <I>output</I> without modification.
  <P>
  The user must supply values for the query parameters ra, dec, and one or
  more of the size query parameters width, ra/xwidth, dec/ywidth, hwidth,
  ra/xhwidth, dec/yhwidth, or radius by
  specifying appropriate values for the <I>ra</I>, <I>dec</I>, and <I>size</I>
  parameters in the units expected by the catalog query. These values are
  treated as strings and passed directly to the catalog query without
  coordinate transformations or units conversions.
  <P>
  The catalog configuration file <I>catdb</I> contains a record for each
  supported <I>catalog</I>. This record contains the catalog address,
  the query format, and the output format. The default configuration file
  is "<TT>astcat$lib/catdb.dat</TT>".
  <P>
  The output of adumpcat can be used to refine the catalog record in the
  catalog configuration file.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. List the supported catalogs, select a catalog to query, make the query,
  and capture the results. The aclist task is used to list the supported
  catalogs, as well as to list the query and output formats for the selected
  catalog as shown below. The query format tells the user that the input
  ra and dec must be entered in J2000 sexagesimal hours and degrees and
  that the size parameter is a halfwidth in minutes.  In this case the
  results containing leading and trailing comments and
  HTML markup as shown below.
  <P>
  <PRE>
  cl&gt; aclist *
  usno2@noao
  <P>
  cl&gt; aclist usno2@noao verb+
  Scanning catalog database astcat$lib/catdb.dat
  Listing the supported catalogs
  usno2@noao
  nquery 4
      ra 00:00:00.00 hours %0.2h
      dec 00:00:00.0 degrees %0.1h
      hwidth 5.0 minutes %0.1f
      qsystem J2000.0 INDEF %s
  nheader 1
      csystem J2000.0
  nfields 4
      ra 1 0 d hours %12.3h
      dec 2 0 d degrees %12.2h
      mag1 3 0 r INDEF %4.1f
      mag2 4 0 r INDEF %4.1f
  <P>
  cl&gt; adumpcat usno2@noao2 m51.res 13:29:53.27 +47:11:48.4 10.0
  <P>
  cl&gt; page m51.res
  <P>
  HTTP/1.1 200 OK^M
  Date: Mon, 27 Mar 2000 20:59:46 GMT^M
  Server: Apache/1.2.6^M
  Connection: close^M
  Content-Type: text/html^M
  ^M
  <P>
  &lt;HTML&gt;&lt;HEAD&gt;&lt;TITLE&gt;USNO search results&lt;/TITLE&gt;&lt;BODY&gt;
  &lt;body bgcolor="#FFF9E6"&gt;&lt;H1&gt;USNO extraction (00:00:00.0 :00:00:00)&lt;/H1&gt;&lt;P&gt;
  Output columns are RA, DEC, Red mag. (E/F) , and Blue mag. (O/J)&lt;P&gt;
  &lt;P&gt;&lt;H2&gt;Region number  Z= 825 RA(           0:       60000)  SPD(    32339999:
   32460000)&lt;/H2&gt;&lt;P&gt;
   00:00:01.443   -0:06:57.52  13.5  15.2&lt;BR&gt;
   00:00:01.574   -0:05:33.26  16.1  18.0&lt;BR&gt;
   ...
   00:00:39.326   -0:00:47.83  14.6  16.9&lt;BR&gt;
   00:00:39.650   -0:02:02.64  18.8  19.4&lt;BR&gt;
  &lt;P&gt;&lt;H2&gt;Region number  Z= 825 RA(   129539999:   129600000)  SPD(    32339999:
   32460000)&lt;/H2&gt;&lt;P&gt;
   23:59:20.351   -0:09:34.07  18.3  19.5&lt;BR&gt;
   23:59:21.065   -0:01:18.44  17.4  19.1&lt;BR&gt;
   23:59:59.737   -0:03:54.75  10.5  12.4&lt;BR&gt;
   23:59:59.930   -0:01:57.84  18.1  18.6&lt;BR&gt;
  &lt;P&gt;&lt;H2&gt;Region number  Z= 900 RA(           0:       60000)  SPD(    32400000:
   32460000)&lt;/H2&gt;&lt;P&gt;
   00:00:00.503    0:06:07.90  18.0  19.5&lt;BR&gt;
   00:00:02.568    0:05:07.93  18.3  19.4&lt;BR&gt;
   00:00:39.056    0:02:11.91  18.4  19.2&lt;BR&gt;
   00:00:39.978    0:09:54.59  18.6  19.5&lt;BR&gt;
  &lt;P&gt;&lt;H2&gt;Region number  Z= 900 RA(   129539999:   129600000)  SPD(    32400000:
  32460000)&lt;/H2&gt;&lt;P&gt;
   23:59:21.198    0:07:43.82  18.7  19.3&lt;BR&gt;
   23:59:21.364    0:08:05.09  18.4  19.6&lt;BR&gt;
   23:59:57.729    0:03:36.13  18.0  19.2&lt;BR&gt;
   23:59:59.460    0:08:42.02  19.2  19.7&lt;BR&gt;
  &lt;HR&gt;&lt;P&gt;&lt;P&gt; Found       193 Entries&lt;P&gt;&lt;HR&gt;
  &lt;address&gt;
    Central Computer Services, National Optical Astronomy Observatories,
    950 N. Cherry Ave., P.O. Box 26732,
    Tucson, AZ  85726, Phone: 520-318-8000, FAX: 520-318-8360
    &lt;P&gt;Updated: 04Aug1998&lt;/address&gt;&lt;/body&gt;&lt;/html&gt;
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
  aclist, agetcat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
