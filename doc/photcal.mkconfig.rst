.. _mkconfig:

mkconfig — Prepare a configuration file
=======================================

**Package: photcal**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkconfig -- create a new configuration file 
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkconfig config 
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>config</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='config' Line='config'>
  <DD>The name of the new configuration file.
  </DD>
  </DL>
  <DL>
  <DT><B>catalog</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catalog' Line='catalog'>
  <DD>The source of the standard star catalog format description.
  <I>Catalog</I> may be one of the supported standard star
  catalogs maintained
  in the directory "<TT>photcal$catalogs/</TT>", a catalog created with
  MKCATALOG, the standard input "<TT>STDIN</TT>",
  or a file created by the user containing the catalog
  format description.
  <I>Catalog</I> is not prompted for if <I>template</I> is "<TT></TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>observations</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='observations' Line='observations'>
  <DD>The source of the observations file format description.
  <I>Observations</I> may be a catalog created by MKNOBSFILE,
  MKOBSFILE, OBSFILE, or MKCATALOG, the standard input "<TT>STDIN</TT>",
  or a file created by the user containing the observations file format
  description. <I>Observations</I> is not prompted for if <I>template</I> is "<TT></TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>transform </B></DT>
  <! Sec='PARAMETERS' Level=0 Label='transform' Line='transform '>
  <DD>The source of the transformation equations definition.
  <I>Transform</I> may be the name of one of the supported standard star
  catalogs maintained in the directory "<TT>photcal$catalogs/</TT>",
  the standard input "<TT>STDIN</TT>", or a file created by the user
  containing the transformation equations definition.
  <I>Transform</I> is not prompted for if <I>template</I> is "<TT></TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>template = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='template' Line='template = ""'>
  <DD>The name of an existing configuration file that can be used as a template
  for the new configuration file.
  If <I>template</I> is the null string "<TT></TT>", then MKCONFIG
  prompts the user for the source of the standard star catalog 
  and observations file format descriptions
  <I>catalog</I> and <I>observations</I>, and the source of the transformation
  equation definitions <I>transform</I>.
  If <I>template</I> exists,
  MKCONFIG copies <I>template</I> into <I>config</I> and enters the editor
  if <I>edit</I> is "<TT>yes</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B>catdir = "<TT>)_.catdir</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='catdir' Line='catdir = ")_.catdir"'>
  <DD>The directory containing the supported standard star catalogs.
  The default parameter value  redirects <I>catdir</I>
  to a package parameter of the same name. A list of standard
  catalogs may be obtained by printing the file "<TT>photcal$catalogs/README</TT>".
  Alternatively the user may create their own standard star catalogs 
  and standard star catalog directory.
  </DD>
  </DL>
  <DL>
  <DT><B>verify = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = no'>
  <DD>Verify each new entry in the configuration file as it is entered?
  </DD>
  </DL>
  <DL>
  <DT><B>edit = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='edit' Line='edit = yes'>
  <DD>Enter the editor and review the new configuration file?
  </DD>
  </DL>
  <DL>
  <DT><B>check = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='check' Line='check = yes'>
  <DD>Check the new configuration file for semantic and syntax errors?
  </DD>
  </DL>
  <DL>
  <DT><B>verbose = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verbose' Line='verbose = no'>
  <DD>Print detailed information about the results of the check step instead
  of only a short summary?
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  MKCONFIG is a script task which creates and/or edits the configuration
  file <I>config</I>. If the configuration file already
  exists MKCONFIG, quits with a warning message. If the configuration file is
  a new file, MKCONFIG either prompts the
  user for input if <I>template</I> = "<TT></TT>", or copies the existing configuration
  file <I>template</I> into <I>config</I>.
  <P>
  If <I>template</I>  is "<TT></TT>", MKCONFIG prompts the user for:
  1) the source of the standard star catalog format description
  <I>catalog</I>, which assigns names to the columns of the standard star
  catalog,
  2) the source of the observations file format description
  <I>observations</I>, which assigns names to the columns of the observations file,
  3) and the source of the transformation equations <I>transform</I>, which
  defines the form of the transformation equations from the
  instrumental to the standard system.
  <P>
  If <I>catalog</I>, <I>observations</I>, or <I>transform</I>
  are set to the standard input "<TT>STDIN</TT>", MKCONFIG prompts for input from
  the terminal, verifying the input as it is entered if <I>verify</I> is "<TT>yes</TT>". 
  <P>
  If <I>catalog</I> is a standard star catalog name or a file name,
  MKCONFIG searches 1) the current directory for the associated format
  description file "<TT>fcatalog.dat</TT>", 2) the directory
  <I>catdir</I> for the format description file "<TT>fcatalog.dat</TT>",
  and 3) the current directory for a file called "<TT>catalog</TT>", in that order.
  <I>Catalog</I> is usually one of the supported standard star catalogs or
  a standard star catalog created by the user with MKCATALOG. 
  <P>
  If <I>observations</I> is an observations file name or a file name,
  MKCONFIG searches 1) the current directory for the format
  description file "<TT>fobservations.dat</TT>", and 2)
  the current directory for a file called "<TT>observations</TT>", in that order.
  <I>Observations</I> is usually created by the user with MKNOBSFILE or MKOBSFILE.
  <P>
  If <I>transform</I> is assigned a standard star catalog name or a file name,
  MKCONFIG searches 1) the directory
  <I>catdir</I> for the transformation equations definition file
  "<TT>ttransform.dat</TT>", and 2)
  the current directory for a file called "<TT>transform</TT>", in that order.
  <I>Transform</I> is usually one of the supported standard star catalogs or
  "<TT>STDIN</TT>".
  <P>
  The default photometric standards directory is "<TT>photcal$catalogs/</TT>".
  A list of supported catalogs is shown below.
  The standard catalog format description files may be listed or
  printed with the commands
  "<TT>dir photcal$catalogs/f*.dat</TT>" or "<TT>lprint photcal$catalogs/f*.dat</TT>" respectively.
  The standard transformation equation definition files may be listed or
  printed with
  the commands "<TT>dir photcal$catalogs/t*.dat</TT>" or "<TT>lprint photcal$catalogs/t*.dat</TT>"
  respectively.
  <P>
  After data entry, and if <I>edit</I> is "<TT>yes</TT>",
  MKCONFIG enters the default text editor defined by the
  IRAF environment variable <I>editor</I>.  Small
  corrections to the configuration file may be made at this point.
  Next the configuration file is checked for semantic and syntax errors
  if <I>check</I> is "<TT>yes</TT>" and the results are written on the terminal. 
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Standard catalog format and transform files</H3>
  <! BeginSection: 'STANDARD CATALOG FORMAT AND TRANSFORM FILES'>
  <UL>
  <P>
  The list of standard star catalog files, catalog format description files
  and transformation equation definitions files is presented below.
  <P>
  <PRE>
  	# catalogs	# formats		# transformations
  <P>
  	landolt.dat	flandolt.dat		tlandolt.dat
  </PRE>
  <P>
  </UL>
  <! EndSection:   'STANDARD CATALOG FORMAT AND TRANSFORM FILES'>
  <H3>The configuration file</H3>
  <! BeginSection: 'THE CONFIGURATION FILE'>
  <UL>
  <P>
  The <I>configuration file</I> is a text file which describes how the input data
  is organized in the input files, and defines the form of the transformation
  equations required to convert from the instrumental to the standard system.
  <P>
  The input data is assumed to come from two sources,
  standard star catalogs known as <I>catalogs</I>
  and <I>observations</I> files.
  The <I>catalog</I> files contain the standard indices of a set of standard
  stars, referenced in the catalog by a name called the
  matching name.
  The <I>observations</I> files contain the instrumental magnitudes or colors of
  a subset of the standard stars and/or program stars, also referenced by a
  matching name.
  The names of the observed standard stars must match the names in the
  standard star catalog.  The matching names must be stored in column 1
  in both the catalog and observations files.
  <P>
  The configuration file is divided up into three sections: the <I>catalog
  section</I> which describes the format of the catalog files, the
  <I>observations section</I> which describes the format of the observation 
  files, and the <I>transformation section</I> which defines the
  transformation equations. The catalog section must always appear before the
  observation section, and the observation section must always appear before the
  transformation section.
  <P>
  The <I>catalog and observations sections</I> are used to assign
  names to the columns in the input catalog and observations files. 
  These columns may later be referenced by name and the names used
  as variables in the transformation equations.
  <P>
  The <I>transformation section</I> is used to define the
  transformation equations,
  to specify which parameters are to be varied and which are to be held constant
  during the fitting process,
  and to assign initial values to all the parameters.
  Any number of transformation equations may be defined in
  the transformation section.
  <P>
  The transformation section may also be used to, OPTIONALLY,
  define temporary variables (the set equations), define explicitly
  the derivatives of the transformation equations to be fit with respect
  to the parameters (derivative equations
  and delta declarations), define expressions for the weights and
  errors (weight and error equations), and define an expression to be
  plotted (the plot equation).
  <P>
  For a detailed description
  of the grammar and syntax of the configuration file type <I>"help config"</I>.
  <P>
  The following examples show typical configuration files for two different types
  of photometric calibrations.
  <P>
  <P>
  <I>Example 1</I>. A sample configuration file for reducing UBV photoelectric
  photometry. Note that the instrumental magnitudes are all on the right-hand
  side of the transformation equation and that the standard magnitudes and colors
  are all
  on the left-hand side. Once the values of the transformation equation
  parameters are computed by FITPARAMS using observations of the standard stars,
  standard magnitudes and colors for the program stars can be computed simply by
  evaluating the right-hand side of the transformation equation using
  the task EVALFIT. In this type of setup the equations are fit separately
  and evaluated separately. Note also the use of the error column declarations
  in the observation section, and the use of the const statement to fix the
  values of some parameters.
  <P>
  <PRE>
  # Configuration file for reducing UBV photoelectric photometry.
  <P>
  catalog
  <P>
  V	2		# V magnitude
  BV	3		# B - V color
  UB	4		# U - B color
  <P>
  observation
  <P>
  v		2		# v instrumental magnitude
  b 		3		# b instrumental magnitude
  u 		4		# u instrumental magnitude
  error(v)	5		# error in v instrumental magnitude
  error(b) 	6		# error in b instrumental magnitude
  error(u) 	7		# error in u instrumental magnitude
  X		8		# airmass		
  <P>
  transformation
  <P>
  fit	v1 = 0.0, v2=0.16, v3=-0.043
  const	v4 = 0.0
  VFIT:   V = v1 + v - v2 * X + v3 * (b - v) + v4 * X * (b - v)
  <P>
  fit	b1 = 0.0, b2=0.09, b3=1.266
  const	b4 = 0.0
  BVFIT:  BV = b1 - b2 * X + b3 * (b - v) + b4 * X * (b - v)
  <P>
  fit	u1 = 0.0, u2=0.300, u3=0.861
  const	u4 = 0.0
  UBFIT:  UB = u1 - u2 * X + u3 * (u - b) + u4 * X * (u - b)
  </PRE>
  <P>
  <P>
  <I>Example 2</I>. A sample configuration file for reducing UBV CCD photometry.
  Note that the instrumental magnitudes are all on the left-hand side of the
  transformation equations and the standard star magnitudes and colors
  are all on the right-hand
  side. Once the values of the transformation equation parameters have been
  computed by FITPARAMS using observations of the standard stars, the
  standard magnitudes and colors of the program stars
  can be computed by inverting the system of equations using the task
  INVERTFIT.
  In this type of setup the equations are fit independently, but evaluated
  as a system.
  Note also that the telescope filter slots 1, 2 and 3 were assigned to
  filters v, b and u respectively which is why MKNOBSFILE assigned the names
  m1, m2, m3 to v, b, and u respectively. The user can change these if desired.
  Note also the use of the error declaration statements in both the catalog
  and the observations section.
  <P>
  <PRE>
  catalog
  <P>
  V		2	# V magnitude
  BV		3	# B - V color
  UB		4	# U - B color
  error(V)	5	# error in V magnitude
  error(BV)	6	# error in B-V color
  error(UB)	7	# error in U-B color
  <P>
  observation
  <P>
  ut1		3	# ut time of filter 1 observation
  X1		4	# airmass of filter 1 observation
  m1		7	# filter 1 instrumental magnitude
  error(m1)	8	# error in filter 1 instrumental magnitude
  ut2		10	# ut time of filter 2 observation
  X2		11	# airmass of filter 2 observation
  m2	 	14	# filter 2 instrumental magnitude
  error(m2) 	15	# error in filter 2 instrumental magnitude
  ut3		17	# ut time of filter 3 observation
  X3	        18	# airmass of filter 3 observation		
  m3	 	19	# filter 3 instrumental magnitude
  error(m3) 	20	# error in filter 3 instrumental magnitude
  <P>
  <P>
  transformation
  <P>
  fit   u1 = 0.0, u2=0.68, u3=0.060
  UFIT: m3 = u1 + V + BV + UB + u2 * X3 + u3 * UB
  <P>
  fit   b1 = 0.0, b2=0.30, b3=0.010
  BFIT: m2 = b1 + V + BV + b2 * X2 + b3 * BV
  <P>
  fit   v1 = 0.0, v2=0.15, v3=0.000
  VFIT: m3 = v1 + V + v2 * X3 + v3 * BV
  </PRE>
  <P>
  </UL>
  <! EndSection:   'THE CONFIGURATION FILE'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Type in from scratch a new configuration file to reduce some UBV
  photoelectric photometry. The catalog and observations file are simple
  text files written with the user's own data acquisition software, whose
  format is known by the user.
  <P>
  <PRE>
      ph&gt; mkconfig ubv.cfg
  <P>
          ... answer "STDIN" in response to the query for the catalog
  	    parameter, and enter the standard star catalog format
  	    description as prompted
  <P>
  	... a sample input session is shown below, note that in this
  	    examine &lt;EOF&gt; is implemented as ^Z
  <P>
      ENTER THE STANDARD STAR CATALOG FORMAT DESCRIPTION
   
      Enter column definition (name number, ?=help, &lt;EOF&gt;=quit entry): V 2
      Enter column definition (name number, ?=help, &lt;EOF&gt;=quit entry): BV 3
      Enter column definition (name number, ?=help, &lt;EOF&gt;=quit entry): UB 4
      Enter column definition (name number, ?=help, &lt;EOF&gt;=quit entry): ^Z
    
  	... answer "STDIN" in response to the query for the
  	    observations parameter, and enter the observations file
  	    format description as prompted
  <P>
  	... a sample input session is shown below, note that in this
  	    example &lt;EOF&gt; is implemented as ^Z
  <P>
      ENTER THE OBSERVATIONS FILE FORMAT DESCRIPTION
  <P>
      Enter column definition (name number, ?=help, &lt;EOF&gt;=quit entry): v 2
      Enter column definition (name number, ?=help, &lt;EOF&gt;=quit entry): b 3
      Enter column definition (name number, ?=help, &lt;EOF&gt;=quit entry): u 4
      Enter column definition (name number, ?=help, &lt;EOF&gt;=quit entry): X 5
      Enter column definition (name number, ?=help, &lt;EOF&gt;=quit entry): ^Z
  <P>
  	... answer "STDIN" in response to the query for the
  	    transform parameter, and enter the transformation
  	    equations as prompted
  <P>
  	... a sample input session is shown below for a single equation is
  	    shown below, note that in this example &lt;EOF&gt; is implemented as
  	    ^Z
  <P>
      ENTER THE TRANSFORMATION EQUATIONS
  <P>
      Enter the label and functional form for EQUATION 1
  <P>
      Enter label (e.g. VFIT) (label, ?=help, &lt;EOF&gt;=quit entry): VFIT
      Enter equation (equation, equation\=continue, ?=help, &lt;EOF&gt;=quit entry):
      V = v + v1 + v2 * X + v3 * (b - v)
  <P>
      Enter initial values for the parameters to be fit in EQUATION 1
  <P>
      Enter parameter 1 (name value, ?=help, &lt;EOF&gt;=quit entry):v1 25.
      Enter parameter 2 (name value, ?=help, &lt;EOF&gt;=quit entry):v2 -.15
      Enter parameter 3 (name value, ?=help, &lt;EOF&gt;=quit entry):v3 1.06
      Enter parameter 4 (name value, ?=help, &lt;EOF&gt;=quit entry):^Z
      
      Enter initial values for the parameters to be held constant in
      EQUATION 1
  <P>
      Enter parameter1 and value (name value, ?=help, &lt;EOF&gt;=quit entry):^Z
       
      Enter the label and functional form for EQUATION 2
  <P>
      Enter label (e.g. VFIT) (label, ?=help, &lt;EOF&gt;=quit entry): BFIT 
  <P>
  	... after the program enters the editor make any small changes
  	    required
  <P>
  	... examine the final output for errors
  <P>
      ph&gt; edit ubv.cfg
  <P>
  	... correct any errors with the editor
  <P>
      ph&gt; chkconfig ubv.cfg
  <P>
  	... check the newly edited file for errors
  <P>
  </PRE>
  <P>
  2. Create a configuration file to reduce some JHK photometry. In this
  example the user has created a JHK standard star catalog called jhkcat
  using the task MKCATALOG, an observations file called jhkobs
  using the task MKNOBSFILE, and has decided to type in the transformation
  equations by hand using the default editor.
  <P>
  <PRE>
  	ph&gt; mkconfig jhk.cfg jhkcat jhkobs
  <P>
  	    ... answer "STDIN" in response to the query for the
  	        transform parameter, followed by &lt;EOF&gt;, usually ^Z
  		to terminate prompting for the transformation equations
  <P>
  	    ... use the editor to enter the transformation equations
  <P>
  	    ... check the result for errors
  <P>
  	ph&gt; edit jhk.cfg
  <P>
  	    ... correct errors found in previous run using the editor
  <P>
  	ph&gt; chkconfig jhk.cfg
  <P>
  	    ... check the edited file for errors
  </PRE>
  <P>
  3. Create a new configuration file for reducing some UBVR photometry, using 
  the UBVR standards in the landolt UBVRI standard star catalog. The standard
  star observations file "<TT>stdobs</TT>" was created with the task MKNOBSFILE.
  <P>
  <PRE>
  	ph&gt; mkconfig ubvr.cfg landolt stdobs landolt
  <P>
  	    ... read in the catalog format description for the
  	        landolt UBVRI standards catalog
  <P>
  	    ... read in the observations file format description
  	        created by a previous run of mknobsfile
  <P>
  	    ... read in the sample transformation description file for the
  		landolt UBVRI system
  <P>
  	    ... use the editor to delete any references to catalog
  	        variables that are not going to be used in the
  		transformation equations, and to edit the transformation
  		equations as desired
  <P>
  	    ... check the result for errors
  <P>
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
  edit,chkconfig,mknobsfile,mkobsfile
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'STANDARD CATALOG FORMAT AND TRANSFORM FILES' 'THE CONFIGURATION FILE' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
