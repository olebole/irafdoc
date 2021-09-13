afiltcat — Filter astrometry files derived from astrometric catalogs
====================================================================

**Package: astcat**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>afiltcat (Mar00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>astcat</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>afiltcat (Mar00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>afiltcat</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  afiltcat -- filter astrometry files
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  afiltcat input output
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_input">input</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>The list of input astrometry files. Astrometry files may be created by
  other astcat tasks, e.g. agetcat, in which case they are preceded by a
  header describing the format of the input astrometry file, or by
  other IRAF or user tasks in which case the <I>acatpars</I> parameter set
  must be used to describe them.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_output">output </A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output '>
  <DD>The list of output astrometry files. The number of output astrometry files
  must be equal to the number of input astrometry files. If the output file
  name equals the input file name then the original astrometry file is
  overwritten.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_acatpars">acatpars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='acatpars' Line='acatpars = ""'>
  <DD>The default input astrometry file format parameters. The acatpars parameters
  are used only if the input astrometry file does not have a header. Type
  "<TT>help acatpars</TT>" for a detailed description of the acatpars parameters.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_catalogs">catalogs = "<TT>filename@noao</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catalogs' Line='catalogs = "filename@noao"'>
  <DD>The dummy input catalog name. Afiltcat task users should leave this
  parameter at its default setting.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_standard">standard = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='standard' Line='standard = yes'>
  <DD>Output a standard astrometry file ? If standard = yes then a header describing
  the format of the output astrometry file is written to the output file.
  Astcat package tasks use this information to decode the astrometry file. If
  standard = no, no header is written and astcat tasks must use the acatpars
  parameters to decode the astrometry file.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_filter">filter = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='filter' Line='filter = yes'>
  <DD>Filter rather than copy the input astrometry file to the output astrometry
  file ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_afiltpars">afiltpars = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='afiltpars' Line='afiltpars = ""'>
  <DD>The astrometry file filtering parameter set. Afiltpars parameters permit the
  user to sort the output on a field or field expression, select or reject
  catalog records using a boolean expression, select or reject fields
  to output, add new fields to the output that are expressions of existing
  fields, and perform simple coordinate transformations.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_update">update = no</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = no'>
  <DD>Update the default values of the algorithm parameter sets, e.g. acatpars and
  afiltpars, on task termination ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_verbose">verbose = yes</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = yes'>
  <DD>Print status messages on the terminal as the task proceeds ?
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_catdb">catdb = "<TT>)_.catdb</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catdb' Line='catdb = ")_.catdb"'>
  <DD>The catalog configuration file. Catdb defaults to the value of the
  package parameters catdb. The default catalog configuration file is
  "<TT>astcat$lib/catdb.dat</TT>".
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  Afiltcat filters the list of input astrometry files <I>input</I>
  and writes the results to the output files <I>output</I>. The number of input
  astrometry files must equal the number of output astrometry files.
  <P>
  The format of the input astrometry files is defined by the file header
  if the file was written by an astcat package task, or by the
  <I>acatpars</I> parameter set. The acatpars parameters <I>ftype</I> and
  <I>csystem</I> define the input astrometry file type and coordinate system.
  The position, size, and units of the standard astrometry file fields
  the associated error fields are defined by the parameters:
  <I>id</I>, <I>ra</I>, <I>dec</I>, <I>pmra</I>, <I>pmdec</I>, <I>catsystem</I>,
  <I>equinox</I>, <I>epoch</I>, <I>px</I>, <I>rv</I>, <I>mag</I>, <I>color</I>,
  <I>xp</I>, <I>yp</I>, <I>xc</I>, <I>yc</I>, and <I>imag</I>, and:
   <I>era</I>, <I>edec</I>,
  <I>epmra</I>, <I>epmdec</I>, <I>epx</I>, <I>erv</I>, <I>emag</I>, <I>ecolor</I>,
  <I>exc</I>, <I>eyc</I>, <I>eimag</I>.  More detailed information on astrometry
  files and the acatpars parameters can be found by typing "<TT>help files</TT>"
  and "<TT>help acatpars</TT>".
  <P>
  If <I>filter</I> = yes, the input astrometry file is filtered before being
  written to the outputfile. The filtering parameters are defined by the
  filtering parameter set <I>afiltpars</I>.
  The afilterpars parameters permit the user to sort the query results by setting
  the sort field parameter <I>fsort</I>, select or reject
  catalog records by setting the selection expression parameter <I>fexpr</I>,
  select or reject fields for output by setting the output field
  list parameter <I>afields</I>, and change the coordinate system, units,
  and format of the output coordinates by setting the <I>fosystem</I>,
  <I>foraunits</I>, <I>fodecunits</I>, <I>foraformat</I>, and <I>fodecformat</I>
  parameters. A more detailed description of the filtering
  parameters can be obtained by typing "<TT>help afiltpars</TT>".
  <P>
  If <I>standard</I> = yes a header is written to the output file which
  defines the contents and format of the output astrometry file. The astcat
  tasks use this header to decode the astrometry files. If the header is
  missing or has been modified by non-astcat tasks the user must set
  standard = no, and use the <I>acatpars</I> parameters to define the
  astrometry file format. Most non-astcat tasks will interpret the catalog
  header as documentation and skip it.
  <P>
  If <I>update</I> = yes the values of the <I>acatpars</I> and <I>afiltpars</I>
  parameters are updated at task termination. If <I>verbose</I> = yes
  then detailed status reports are issued as the task executes.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Sort the input astrometry file using the value of the magnitude field.
  <P>
  <PRE>
  cl&gt; page reg001.cat.1
  cl&gt; afiltcat reg001.cat.1 reg001.cat.2 fsort=mag1
  </PRE>
  <P>
  2. Repeat example 1 but only output records for which mag1 &lt;= 16.0.
  <P>
  <PRE>
  cl&gt; afiltcat reg001.cat.1 reg001.cat.3 fsort=mag1 fexpr="mag1 &lt;= 16.0"
  </PRE>
  <P>
  3. Repeat example 2 but since the input astrometry file has 2 magnitude
  columns output a new color field equal to "<TT>mag2 - mag1</TT>".
  <P>
  <PRE>
  cl&gt; afiltcat reg001.cat.1 reg001.cat.4 fsort=mag1 fexpr="mag1 &lt;= 16.0" \<BR>
  fields="f[*],mag2-mag1"
  </PRE>
  <P>
  4. Repeat example 1 but overwrite the input astrometry file.
  <P>
  <PRE>
  cl&gt; page reg001.cat.1
  cl&gt; afiltcat reg001.cat.1 reg001.cat.1 fsort=mag1
  </PRE>
  <P>
  <P>
  5. Filter a list of input astrometry files by extracting columns 1-4
  but reversing the order of fields 3 and 4.  Overwrite the input files.
  <P>
  <PRE>
  cl&gt; afiltcat @inlist @inlist fields="f[1-2],f4,f3"
  </PRE>
  <P>
  6. Repeat the previous example for a list of text files which have no catalog
  headers but contain the ras and decs in hours and degrees in J2000
  coordinates of a list of source  in columns 1 and 2 of a simple text file.
  <P>
  <PRE>
  cl&gt; afiltcat @inlist @inlist ftype="stext" csystem=j2000 ra="1 hours" \<BR>
      dec="2 degrees" mag="3-4" fields="f[1-2],f4,f3"
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  aclist, agetcat, acatpars, afiltpars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>