.. _agetcat:

agetcat — Extract astrometry files from astrometric catalogs
============================================================

**Package: astcat**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  agetcat -- Extract objects from astrometric catalogs
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  agetcat regions output
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>regions</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='regions' Line='regions'>
  <DD>The source  of the extraction region definitions. The options are:
  <DL>
  <DT><B>&lt;filename&gt;</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='&lt;filename&gt;'>
  <DD>The name of a text file containing a list of region definitions, one
  region definition per line. The format of the regions file is described
  in detail below.
  </DD>
  </DL>
  <DL>
  <DT><B>&lt;image list&gt;</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line='&lt;image list&gt;'>
  <DD>The list of images containing the region definition. The input images
  must have a valid FITS world coordinate system in order to be used
  for region definition.
  </DD>
  </DL>
  <DL>
  <DT><B>pars</B></DT>
  <! Sec='PARAMETERS' Level=1 Label='pars' Line='pars'>
  <DD>If regions is set to the reserved keyword "<TT>pars</TT>" then a single region
  definition is read from the <I>aregpars</I> parameter set. By default a region
  ten arc minutes in size around coordinates ra = "<TT>00:00:00.0</TT>" and
  dec = "<TT>+00:00:00</TT>" in the query coordinate system is extracted.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>output </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output '>
  <DD>The list of output astrometry files. The number of output files must be equal
  to the number regions in the regions list times the number of astrometry
  catalogs in the catalog list. By default the output files are assigned names of
  the form "<TT>reg#[.cat#].cat.#</TT>" if the region definition source is "<TT>pars</TT>" or
  a file e.g. "<TT>reg002.cat.1</TT>", or "<TT>image[.cat#].cat.#</TT>" if the region
  definition source is an image list, e.g. "<TT>image.cat.1</TT>". The catalog number
  is only inserted if there is more than one catalog in the catalog list.
  </DD>
  </DL>
  <DL>
  <DT><B>aregpars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='aregpars' Line='aregpars = ""'>
  <DD>The region definition parameter set. The aregpars parameters define the
  extraction region center, region width, region center units, and the region
  center coordinate system. The region definition parameters are used if
  <I>regions</I> = "<TT>pars</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>catalogs = "<TT>)_.catalogs</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catalogs' Line='catalogs = ")_.catalogs"'>
  <DD>The list of input astrometry catalogs. By default the catalog name is set to the
  value of the package parameter catalogs. 
  </DD>
  </DL>
  <DL>
  <DT><B>standard = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='standard' Line='standard = yes'>
  <DD>Output a standard astrometry file ? If standard = yes then a header describing
  the format of the astrometry file is written to the output file. The
  astcat package
  tasks use this information to decode the file. If standard = no, no
  header is written and the user must instruct the astcat tasks how to decode the
  file.
  </DD>
  </DL>
  <DL>
  <DT><B>filter = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter' Line='filter = no'>
  <DD>Filter the results of the catalog query before writing the final results
  to the output astrometry file ?
  </DD>
  </DL>
  <DL>
  <DT><B>afiltpars = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='afiltpars' Line='afiltpars = ""'>
  <DD>The astrometry file filtering parameter set. These parameters permit the user
  to sort the output on a field or field expression, select or reject
  catalog records using a boolean expression, select or reject fields
  to output, add new fields that are expressions of existing fields to
  the output, and perform simple coordinate transformations.
  </DD>
  </DL>
  <DL>
  <DT><B>update = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = no'>
  <DD>Update the default values of the algorithm parameters, e.g. aregpars and
  afiltpars, at task termination ?
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print status messages on the terminal as the task proceeds ?
  </DD>
  </DL>
  <DL>
  <DT><B>catdb = "<TT>)_.catdb</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catdb' Line='catdb = ")_.catdb"'>
  <DD>The catalog configuration file. Catdb defaults to the value of the
  package parameter catdb. The default catalog configuration file is
  "<TT>astcat$lib/catdb.dat</TT>".
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  Agetcat extracts astrometry files from local or remote astrometry catalogs
  <I>catalogs</I> using a list of region definitions <I>regions</I> supplied by
  the user and writes the results of each catalog query to the output astrometry
  files <I>output</I>.
  <P>
  A region definition consists of the coordinates of the field center,
  the field size, the units of the field center, and the coordinate system of
  the field center. If <I>regions</I> = "<TT>pars</TT>" these quantities are read
  from the <I>aregpars</I> parameters <I>rcra</I>, <I>rcdec</I>, <I>rcrawidth</I>,
  <I>rcdecwidth</I> <I>rcraunits</I>, <I>rcdecunits</I>., and <I>rcsystem</I>. 
  If <I>regions</I> is an image they are read from the FITS world coordinate
  system in the image header.  If <I>regions</I> is a file name they are
  read from a file whose format is the following.
  <P>
  <PRE>
  # Optional comment
  <P>
  ra1 dec1 xwidth1 ywidth1 [raunits1 [decunits1 [system1]]]
  ra2 dec2 xwidth2 ywidth2 [raunits2 [decunits2 [system2]]]
  raN decN xwidthN ywidthN [raunitsN [decunitsN [systemN]]]
  </PRE>
  <P>
  Quantities in square brackets are optional. If system is undefined the
  coordinate system defaults to the query coordinate system, i.e. if the
  catalog query expects coordinates in J2000.0 then ra and dec will be
  interpreted as though they were in the J2000.0 system. If undefined 
  the ra and dec units default to the preferred units of the coordinate
  system, i.e. hours and degrees for equatorial coordinate systems,
  and degrees and degrees for ecliptic, galactic, and supergalactic 
  coordinate systems.
  <P>
  A sample regions file  is shown below. If the catalog query system is
  J2000.0 then all four region definitions are equivalent, since J2000.0
  is assumed in examples 1 and 2, is specified in example 3, and example 4
  is same region as example 3 but expressed in the B1950.0 coordinate system.
  <P>
  <PRE>
  # List of targets
  <P>
  13:29:53.27 +47:11:48.4 10.0 10.0 
  13:29:53.27 +47:11:48.4 10.0 10.0 hours degrees 
  13:29:53.27 +47:11:48.4 10.0 10.0 hours degrees J2000.0
  13:27:46.90 +47:27:16.0 10.0 10.0 hours degrees B1950.0
  </PRE>
  <P>
  For each specified astrometry catalog in <I>catalog</I> agetcat loops through the
  regions list, formats the catalog query, makes a local or remote
  connection to the catalog server using the catalog description in the
  catalog configuration file <I>catdb</I>, and captures the results.
  Catalog names must be of the forms catalog@site, e.g. usno2@noao.
  Catalog names without entries in the catalog configuration file
  are skipped.
  <P>
  If <I>filter</I> = yes, the captured results are filtered using the
  values of the parameters in the filtering parameter set <I>afiltpars</I>.
  The afilterpars parameters permits the user to sort the query results by setting
  the sort field parameter <I>fsort</I>, select or reject
  catalog records by setting the selection expression parameter <I>fexpr</I>,
  select or reject fields for output by setting the output field
  list parameter <I>fields</I>, and change the coordinate system, units,
  and format of the catalog coordinates by setting the <I>fosystem</I>,
  <I>foraunits</I>, <I>fodecunits</I>, <I>foraformat</I>, and <I>fodecformat</I>
  parameters. A more detailed description of the region filtering
  parameters can be obtained by typing "<TT>help afiltpars</TT>".
  <P>
  If <I>standard</I> = yes a header is written to the output astrometry file which
  defines the contents and format of the output object list. The astcat
  tasks use this header to decode the input catalog files. If it is
  missing or has been modified by non-astcat tasks the user must use
  the <I>acatpars</I> parameters to define the astrometry file format. Most
  non-astcat tasks will interpret the astrometry file header as documentation
  and skip it.
  <P>
  If <I>update</I> = yes the values of the <I>aregpars</I> and <I>afilterpars</I>
  parameters will be updated at task termination. If <I>verbose</I> = yes
  then detailed status reports are issued as the task executes.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Extract data from the default catalog using the default region definition
  and page the results to determine the catalog format, i.e. the number and
  names of the default output fields.
  <P>
  <PRE>
  cl&gt; agetcat pars default
  cl&gt; page reg001.cat.1
  </PRE>
  <P>
  2. Repeat the previous example but sort the output on the sort field "<TT>mag1</TT>".
  <P>
  <PRE>
  cl&gt; agetcat pars default filter+ fsort=mag1
  cl&gt; page reg001.cat.2
  </PRE>
  <P>
  3. Repeat example 2 but output only those records for which mag &lt;= 16.0.
  <P>
  <PRE>
  cl&gt; agetcat pars default filter+ fsort=mag1 fexpr="mag1 &lt;= 16.0"
  cl&gt; page reg001.cat.3
  </PRE>
  <P>
  4. Repeat example 3 but output a new field equal to mag2 - mag3.
  <P>
  <PRE>
  cl&gt; agetcat pars default filter+ fsort=mag1 fexpr="mag1 &lt;= 16.0" \<BR>
  fields="f[*],mag2-mag1"
  cl&gt; page reg001.cat.4
  </PRE>
  <P>
  5. Run agetcat on the text file regions which contains a list of region
  definitions. Note that the coordinate system and coordinate units default
  to those expected by the catalog query. The latter information can be
  determined by running aclist on the default catalog.
  <P>
  <PRE>
  cl&gt; page regions
  00:00:00.0 -90:00:00 10.0 10.0 
  00:00:00.0 -60:00:00 10.0 10.0 
  00:00:00.0 -30:00:00 10.0 10.0 
  00:00:00.0 +00:00:00 10.0 10.0 
  00:00:00.0 +30:00:00 10.0 10.0 
  00:00:00.0 +60:00:00 10.0 10.0 
  00:00:00.0 +90:00:00 10.0 10.0 
  cl&gt; agetcat regions default
  cl&gt; page reg001.cat.5
  cl&gt; page reg002.cat.1
  cl&gt; page reg003.cat.1
  cl&gt; page reg004.cat.1
  cl&gt; page reg005.cat.1
  cl&gt; page reg006.cat.1
  cl&gt; page reg007.cat.1
  </PRE>
  <P>
  6. Repeat example 5 but find data for two catalogs the usno2@noao and
  gsc@cadc.
  <P>
  <PRE>
  page regions
  00:00:00.0 -90:00:00 10.0 10.0 
  00:00:00.0 -60:00:00 10.0 10.0 
  00:00:00.0 -30:00:00 10.0 10.0 
  00:00:00.0 +00:00:00 10.0 10.0 
  00:00:00.0 +30:00:00 10.0 10.0 
  00:00:00.0 +60:00:00 10.0 10.0 
  00:00:00.0 +90:00:00 10.0 10.0 
  cl&gt; agetcat regions default catalogs="usno2@noao,gsc@noao"
  </PRE>
  <P>
  7. Run agetcat on a list of images containing valid FITS WCS information.
  Note that in the following example the test image dev$pix does not
  have a FITS WCS so no data is extracted for it.
  <P>
  <PRE>
  cl&gt; page imlist
  dev$pix
  dev$ypix
  cl&gt; agetcat @imlist default
  cl&gt; page wpix.cat.1
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
  aclist, adumpcat, aregpars, afiltpars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
