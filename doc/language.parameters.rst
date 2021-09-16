.. _parameters:

parameters — Discussion of parameter attributes
===============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  parameters -- IRAF parameters and their usage
  </UL>
  <! EndSection:   'NAME'>
  <H3>Discussion</H3>
  <! BeginSection: 'DISCUSSION'>
  <UL>
  <P>
  1. <I>Introduction</I>
  <P>
      Parameters are the primary means of communicating information between
  the user and IRAF tasks, and between separate IRAF tasks.  Each user
  effectively has their own copy of the parameters for the tasks they run,
  and by tailoring these as they wish, they may customize the IRAF environment.
  Here we describe characteristics of IRAF parameters.
  The syntax of parameter declarations is described elsewhere.
  <P>
  <P>
  2. <I>Parameter Types</I>
  <P>
      The CL supports a variety of parameter datatypes, from the conventional
  string, integer, and floating point types, to the exotic struct and cursor
  types.  There is no complex type in the CL.
  <P>
  <DL>
  <DT><B>char</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='char' Line='char'>
  <DD>Character parameters are used to store strings of ASCII characters.
  By default character parameters have a maximum length of 64 characters,
  but this may be extended using the <I>length</I> option when the parameter
  is declared.  A character parameter consisting of a single character can
  usually be treated as an integer, with a value equal to the ASCII value
  of the character.
  </DD>
  </DL>
  <DL>
  <DT><B>int</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='int' Line='int'>
  <DD>Integer parameters are used to store integer information.  Integer parameters
  are stored internally as a long integer, permitting at least 32 bits of
  precision.
  </DD>
  </DL>
  <DL>
  <DT><B>real</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='real' Line='real'>
  <DD>Real parameters are stored internally as double's.
  In general they may be entered with or without a decimal point,
  and with or without an exponent.  Note that the exponent should be
  entered using an E not a D.
  </DD>
  </DL>
  <DL>
  <DT><B>bool</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='bool' Line='bool'>
  <DD>Boolean parameters may only have the values <I>yes</I> or <I>no</I>.
  </DD>
  </DL>
  <DL>
  <DT><B>file</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='file' Line='file'>
  <DD>File parameters are basically character parameters which are required
  to be valid file names.  All operations legal on characters are legal
  on file parameters.  Various checks on the accessibility or existence
  of a file may be automatically performed when a <I>file</I> type parameter
  is used at runtime.
  </DD>
  </DL>
  <DL>
  <DT><B>struct</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='struct' Line='struct'>
  <DD>Struct parameters are characters strings which are treated specially by
  the scan and fscan functions.  Scan and fscan set structs to the
  remainder of the line being scanned without further parsing.
  </DD>
  </DL>
  <DL>
  <DT><B>gcur, imcur</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='gcur' Line='gcur, imcur'>
  <DD>The cursor parameters have a character string value with a predefined cursor
  value format.  When a cursor type parameter is read in "<TT>query</TT>" mode, the
  hardware cursor on the graphics terminal or image display is physically read.
  If the cursor parameter is list-structured, cursor input may also be taken
  from a list (text file).  For a more detailed discussion of cursor control
  in the CL, type <I>help cursors</I>.
  </DD>
  </DL>
  <P>
  <P>
  3. <I>List-Directed Parameters</I>
  <P>
      Frequently one may have a list of values, e.g. numbers or file names,
  which one wishes to analyze in turn.  To do this one may use a list-directed
  parameter.  The parameter is defined with its value field set
  to the name of a file containing the list.  The next time it is referenced
  its value will not be the string containing the file name, but rather
  the first value in the list.  Subsequent calls will return later
  values in the list until an end-of-file is reached, at which point
  the parameter will appear to be undefined.  The file may be
  rewound using the p_filename attribute of the parameter.  Assigning the
  null string to a list parameter closes the associated list file.
  <P>
  <PRE>
  	int	*list = "listfile.lis"
  	int	cur_val
  <P>
  	for (i=1;  i &lt; nlist;  i+=1) {
  	    cur_val = list
  	    analyze (cur_val)
  	}
  <P>
  </PRE>
  <P>
  A common usage of struct list-directed parameters is to read files in
  conjunction with the <I>fscan</I> function.  The following example prints
  out a file.
  <P>
  <PRE>
  	struct	*slist = "filer.lis"
  	struct	line
  <P>
  	while (fscan (slist, line) != EOF)
  	    print (line)
  </PRE>
  <P>
  <P>
  4. <I>Modes</I>
  <P>
      The mode of a parameter determines two qualities: whether the parameter
  is prompted for when it is accessed, and whether the parameter is "<TT>learned</TT>",
  i.e. whether its value is saved between invocations of a task.
  <P>
  A hidden parameter is never prompted for unless it is undefined
  or has an illegal value.  A query parameter is prompted for every time
  it is referenced, except that a query parameter which is set on a
  command line is not queried for when it is accessed within that task.
  <P>
  These are the two basic modes, but a parameter may also be defined
  to be automatic.  This means that the parameter will use the mode
  not of the task, but of the package the task is part of, or by the CL.
  When an automatic parameter is referenced the CL searches
  up this hierarchy to find a mode which is not automatic and uses
  this for the mode.  If the mode switch at all levels is automatic
  then the mode is set to hidden.  The mode switch at the task, package
  and CL levels is determined by the VALUE, not the mode, of the
  parameter with the name "<TT>mode</TT>" associated with the task, package or CL.
  <P>
  Query and automatic parameters are learned by default, while hidden parameters
  are not.
  <P>
  <P>
  5. <I>Ranges</I>
  <P>
      The CL supports ranges for integer and real variables, and enumeration
  lists for character strings.  A user may specify either or both of a minimum
  and maximum for numbers, and the CL will reject
  any values which fall out of this range.  Range checking is only
  performed during querying, or inside <I>eparam</I>, not when a value
  is assigned directly.  For an enumerated string the input string
  is matched against any of the enumerated possibilities
  using a minimum-matching technique.  A value with no match is rejected.
  <P>
  <P>
  6. <I>Parameter Attributes</I>
  <P>
      The user may access the different elements of a parameter using
  the parameter attributes.  For some parameters certain of the
  attributes will be meaningless or undefined.
  <P>
  <DL>
  <DT><B>p_name</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='p_name' Line='p_name'>
  <DD>The name of the parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>p_type</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='p_type' Line='p_type'>
  <DD>A string indicating the basic type of the parameter:
  <P>
  <PRE>
  	b	-- boolean
  	i	-- int
  	r	-- real
  	s	-- string/char
  	f	-- file
  	struct	-- struct
  	gcur	-- graphics cursor
  	imcur	-- image cursor=
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B>p_xtype</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='p_xtype' Line='p_xtype'>
  <DD>This is the same as p_type except that the string is prefixed by "<TT>*</TT>"
  if the parameter is list directed.
  </DD>
  </DL>
  <DL>
  <DT><B>p_mode</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='p_mode' Line='p_mode'>
  <DD>A string indicating the mode of the parameter composed of the characters:
  <P>
  <PRE>
  	q  --  query
  	a  --  automatic
  	h  --  hidden
  	l  --  learned
  </PRE>
  </DD>
  </DL>
  <DL>
  <DT><B>p_value</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='p_value' Line='p_value'>
  <DD>The value of the parameter.  For a list-directed parameter this is a
  element in the file, not the file name.  Generally this is what is accessed
  when the parameter attribute is not specified.
  </DD>
  </DL>
  <DL>
  <DT><B>p_length</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='p_length' Line='p_length'>
  <DD>For string type parameters (i.e. char, struct, file, gcur, imcur),
  the maximum length of the string.
  </DD>
  </DL>
  <DL>
  <DT><B>p_mimimum</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='p_mimimum' Line='p_mimimum'>
  <DD>The minimum value for a parameter.  Also for enumerated strings
  the enumeration list.
  </DD>
  </DL>
  <DL>
  <DT><B>p_maximum</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='p_maximum' Line='p_maximum'>
  <DD>The maximum value for a parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>p_filename</B></DT>
  <! Sec='DISCUSSION' Level=0 Label='p_filename' Line='p_filename'>
  <DD>For list-directed parameters the file name associated with the parameter.
  </DD>
  </DL>
  <P>
  <P>
  Attributes may appear on either side of an equals sign, e.g.
  <P>
  <PRE>
  	list.p_filename = "test.fil"
  	= str.p_length
  	range = integ.p_maximum - integ.p_minimum
  	list.p_xtype =
  	= system.page.first_page.p_minimum	# Fully qualified.
  </PRE>
  <P>
  It is illegal to assign to the p_name, p_type and p_xtype fields.
  Most of the direct use of the parameter attributes is expected to be
  in systems level programming.
  <P>
  <P>
  7. <I>Arrays</I>
  <P>
      The user may define arrays of arbitrary dimensionality within the CL.
  The arrays are referenced in the conventional fashion with
  the index list enclosed in square brackets, and the individual
  elements separated by commas.  In their internal representation,
  arrays are similar to those in Fortran, with the first element
  changing fastest as one traverses memory.  The limits of
  each index may be specified.
  <P>
  In general the CL can only access one element of the array at a time
  but there is an automatic looping feature which permits the
  appearance of array arithmetic.  Any executable statement
  in which an array is referenced but  in which the exact element of the array
  is not defined (an "<TT>open</TT>" array reference)
  will cause the CL to implicitly execute that
  statement within a loop over all the elements of the array.  More
  than one "<TT>open</TT>" array may appear in the expression but they
  agree on the limits of the loop.  For example,
  <P>
  <PRE>
  	real x[20,20], y[20], z[10,20], t[20]
  <P>
  	y = x[1,*]
  	t = log(y)
  	z = x[1:10,*]
  </PRE>
  <P>
  <P>
  8. <I>Scope</I>
  <P>
      A parameter is known via an implicit reference if the task in which
  it is defined is active.  In an implicit reference the parameter
  name only, without a task or package qualifier, is given.  The CL
  is always active, so that its parameters are always known.  In a
  script, the script itself is active, so its parameters may be used
  implicitly.  If the script calls another task, that sub-task may
  reference the invoking tasks parameters implicitly.
  <P>
  For an explicit reference, i.e. with task and package qualifiers,
  the parameter is known if the package in which the task is defined
  is active.  For example, when starting the CL, the "<TT>lists</TT>" package
  is not active, thus the parameters of the "<TT>sort</TT>" task may not
  be referenced even in the form "<TT>lists.sort.param</TT>".  However since
  the system package is activated during login to the CL, the parameters
  of "<TT>page</TT>" may be referenced by "<TT>page.param</TT>".  In general a package
  qualifier is used only to remove ambiguity between tasks with the
  same name in two different packages.
  <P>
  <P>
  9. <I>Storage</I>
  <P>
      There are several places in which parameters are stored.
  On disk the CL searches
  for the parameters for a task in three locations.  For a procedure
  script, the default parameters are found in the script file itself, while
  other scripts and executables have a parameter file with defaults in
  the same directory as the script or executable.  These default values
  are used the first time a task is run, or whenever the default values
  have been updated more recently than the user's copy of the parameters.
  The user's copy is created when a task terminates, and retains any
  "<TT>learned</TT>" changes to the parameters.  It is created in a directory
  pointed to by the IRAF logical "<TT>uparm</TT>" which is usually a sub-directory
  of the default IRAF directory for the user.
  <P>
  The user may also use in-core storage for the parameters using
  the cache command.  This keeps parameters for frequently used tasks
  available without requiring disk access.  Cached parameters
  are copied to disk when the CL exits, or when the update command
  is used.
  </UL>
  <! EndSection:   'DISCUSSION'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  lparam, eparam, cache, unlearn, update, cursor
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'DISCUSSION' 'SEE ALSO'  >
  
