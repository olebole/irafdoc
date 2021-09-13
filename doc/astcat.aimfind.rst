.. _aimfind:

aimfind — Select images containing catalog objects
==================================================

**Package: astcat**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  aimfind -- Select images containing catalog data and predict pixel coordinates
  for the catalog objects
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  aimfind images output imfile
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>The input image list. The input images must contain a valid fits world
  coordinate system which is used to determine the catalog extraction region.
  </DD>
  </DL>
  <DL>
  <DT><B>output </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output '>
  <DD>The list of output astrometry file names.  The number of output file names
  must be equal to the number of input images. Output files are only created
  if at least one catalog object is in the image. By default the output files
  are assigned names of the form "<TT>image.cat.#</TT>", e.g. "<TT>image.cat.1</TT>". 
  </DD>
  </DL>
  <DL>
  <DT><B>imfile</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='imfile' Line='imfile'>
  <DD>The list of images containing catalog data.
  </DD>
  </DL>
  <DL>
  <DT><B>catalogs = "<TT>)_.catalogs</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catalogs' Line='catalogs = ")_.catalogs"'>
  <DD>The input astrometry catalog. By default the catalog name is set to the
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
  <DT><B>append = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='append' Line='append = no'>
  <DD>By default the predicted pixel coordinates are prepended to each selected
  output file record. If append = yes they are appended to each selected
  record instead.
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
  Aimfind selects those images from the input image list <I>images</I>
  which contain one or more  catalog <I>catalogs</I> objects and writes
  the resulting catalog records along with predicted pixel coordinates to
  <I>output</I> and the selected image name to <I>imfile</I>. The input images
  must contain a valid FITs wcs.
  <P>
  For each input image aimfind determines the region of the sky covered 
  by the image, formats the appropriate catalog query, makes a local or remote
  connection to the catalog server using the catalog description in the
  catalog configuration file <I>catdb</I>, and captures the results.
  Catalog names must be of the form catalog@site, e.g. lan92@noao.
  <P>
  If <I>filter</I> = yes, the captured results are filtered using the
  values of the parameters in the filtering parameter set <I>afiltpars</I>.
  The afilterpars parameters permit the user to sort the query results by setting
  the sort field parameter <I>fsort</I>, select or reject
  catalog records by setting the selection expression parameter <I>fexpr</I>,
  select or reject fields for output by setting the output field
  list parameter <I>fields</I>, and change the coordinate system, units,
  and format of the catalog coordinates by setting the <I>fosystem</I>,
  <I>foraunits</I>, <I>fodecunits</I>, <I>foraformat</I>, and <I>fodecformat</I>
  parameters. At present the names, data types, units, and format of the
  predicted pixel coordinates computed by aimfind are fixed at "<TT>xp,yp</TT>",
  "<TT>d,d</TT>", "<TT>pixels,pixels</TT>", and "<TT>%10.3f,%10.3f</TT>" respectively. A more detailed
  description of the region filtering parameters can be obtained by typing
  "<TT>help afiltpars</TT>".
  <P>
  If <I>standard</I> = yes a header is written to the output astrometry file which
  defines the contents and format of the output object list. The astcat
  tasks use this header to decode the input catalog files. If it is
  missing or has been modified by non-astcat tasks the user must use
  the <I>acatpars</I> parameters to define the astrometry file format. Most
  non-astcat tasks will interpret the astrometry file header as documentation
  and skip it.
  <P>
  If <I>append</I> = no then the values of the predicted pixel coordinates
  are prepended to each selected catalog record. If append = tes they
  are appended instead.
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
  1. Determine which images in the input image list contain Landolt standards.
  <P>
  <PRE>
  cl&gt; aimfind *.imh "" imlist catalogs=lan92@noao
  cl&gt; page imlist
  </PRE>
  <P>
  2. Repeat the previous example but write an output astrometry file for
  each selected image.
  <P>
  <PRE>
  cl&gt; aimfind *.imh default imlist catalogs=lan92@noao
  </PRE>
  <P>
  3. Repeat example 2 but sort the output on a field called v.
  <P>
  <PRE>
  cl&gt; aimfind *.imh default filter+ fsort="v"
  </PRE>
  <P>
  4. Repeat example 2 but transform the catalog coordinates to the B1950
  system.
  <P>
  <PRE>
  cl&gt; aimfind *.imh default filter+ fosystem="B1950"
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
  aclist, adumpcat, agetcat, afiltpars
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
