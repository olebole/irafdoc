.. _declarations:

declarations — Parameter/variable declarations
==============================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  declarations -- parameter and variable declarations
  </UL>
  <! EndSection:   'NAME'>
  <H3>Syntax</H3>
  <! BeginSection: 'SYNTAX'>
  <UL>
  <PRE>
  vartype [*]varname[index_list] [= init_value] [{options}] [, ...]
  <P>
    or
  <P>
  vartype [*]varname[index_list] [{init_value [, options]}] [, ...]
  </PRE>
  </UL>
  <! EndSection:   'SYNTAX'>
  <H3>Elements</H3>
  <! BeginSection: 'ELEMENTS'>
  <UL>
  <DL>
  <DT><B>vartype</B></DT>
  <! Sec='ELEMENTS' Level=0 Label='vartype' Line='vartype'>
  <DD>One of the legal variable types, i.e.:
  <P>
  	int, bool, char, real, gcur, imcur, struct, file
  </DD>
  </DL>
  <DL>
  <DT><B>varname</B></DT>
  <! Sec='ELEMENTS' Level=0 Label='varname' Line='varname'>
  <DD>The name of the variable or parameter.  The name must begin with
  an alphabetic character or <TT>'_'</TT> and should be fewer than 64 characters
  in length.  If the name is preceded by a <TT>'*'</TT>, then the variable
  is 'list-directed', meaning that a new value is taken from a list
  each time the parameter is read.
  </DD>
  </DL>
  <DL>
  <DT><B>index_list</B></DT>
  <! Sec='ELEMENTS' Level=0 Label='index_list' Line='index_list'>
  <DD>The index_list consists of a series of ranges enclosed in square brackets.
  A range may be a single integer in which case the range is from 1 to
  that integer, or two integers separated by a colon.  The second integer
  must be larger than the first.  Ranges are separated by commas. In
  the special case that no ranges are specified by the user, the variable
  is assumed to be a one-dimensional array with a  range from 1 to the
  number of elements in the initialization list.
  </DD>
  </DL>
  <DL>
  <DT><B>init_value</B></DT>
  <! Sec='ELEMENTS' Level=0 Label='init_value' Line='init_value'>
  <DD>The initialization value is a single value for scalar parameters but
  may be a list for array.  A repetition count may be specified in the form
  <P>
  	rep_count (value)
  <P>
  <P>
  which is equivalent to value repeated the rep_count times.
  The values in the initialization list are separated by commas.
  </DD>
  </DL>
  <DL>
  <DT><B>options</B></DT>
  <! Sec='ELEMENTS' Level=0 Label='options' Line='options'>
  <DD><BR>
  Options define certain characteristics of the variables.  Each
  options has the form opt_name=value where value is a constant.
  The current options are:
  <DL>
  <DT><B>mode</B></DT>
  <! Sec='ELEMENTS' Level=1 Label='mode' Line='mode'>
  <DD>Determines whether the parameter is queried for and whether
  it is learned after task execution.  The default mode for parameters
  declared in the argument list of a CL procedure is "<TT>a</TT>", and "<TT>h</TT>" otherwise.
  </DD>
  </DL>
  <DL>
  <DT><B>min</B></DT>
  <! Sec='ELEMENTS' Level=1 Label='min' Line='min'>
  <DD>The minimum allowable value for the parameter.  If omitted, no min checking
  is performed.
  </DD>
  </DL>
  <DL>
  <DT><B>max</B></DT>
  <! Sec='ELEMENTS' Level=1 Label='max' Line='max'>
  <DD>The maximum allowable value for the parameter.  If omitted, no max checking
  is performed.
  </DD>
  </DL>
  <DL>
  <DT><B>prompt</B></DT>
  <! Sec='ELEMENTS' Level=1 Label='prompt' Line='prompt'>
  <DD><BR>
  The prompt to be used when the parameter is queried for.
  </DD>
  </DL>
  <DL>
  <DT><B>enum</B></DT>
  <! Sec='ELEMENTS' Level=1 Label='enum' Line='enum'>
  <DD>The set of allowable string values for a string valued parameter.
  The character <TT>'|'</TT> delimits successive enumerated strings.
  </DD>
  </DL>
  <DL>
  <DT><B>filetype</B></DT>
  <! Sec='ELEMENTS' Level=1 Label='filetype' Line='filetype'>
  <DD>For a <I>file</I> type parameter, a string containing characters giving
  file characteristics to be checked for when the file parameter is used.
  <DL>
  <DT><B></B></DT>
  <! Sec='ELEMENTS' Level=2 Label='' Line=' '>
  <DD><PRE>
  r	file exists and is readable
  w	file exists and is writable
  n	file does not exist
  b	file is a binary file
  t	file is a text file
  </PRE>
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B>length</B></DT>
  <! Sec='ELEMENTS' Level=1 Label='length' Line='length'>
  <DD>For a string type parameter, the number of characters of storage to
  allocate for the string.  If the actual length of a string later exceeds
  the allocated value the string will be silently truncated.
  </DD>
  </DL>
  <P>
  Note that all string constants in an options list must be enclosed in
  quotes.
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'ELEMENTS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Declaration statements are used for inline declaration of parameters and
  local variables.   A declaration after the begin statement of a procedure
  script is a declaration of a local variable, but any other declaration
  defines a parameter.  Parameters are generally saved between invocations
  of a script while local variables are not.
  <P>
  Parameter and variable declarations should always precede executable
  statements with a script.  Certain functions are legal before
  declarations, but this depends upon certain hidden aspects of
  declarations which are not obvious to the user.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  real	x
  int	ii=32
  int	y {min=0, max=14}
  char	z="abc" {enum="abc|def|ghi", mode="q"}
  <P>
  bool	isotest {YES, mode="ql",
  	    prompt="Do you want to test for isotropy?"}
  <P>
  int	ii=1 {min=0,max=10, prompt="Number of images", mode="h"}
  file	infile="testfile" {filetype="r"}
  struct	line {length=80, mode="h"}
  <P>
  real	array[10]
  int	iarray[15]=1,2,3,4,5,6,7,8,9,10,11,12,13,14,15 {min=0, max=100}
  int	jarray[15] { 5(0), 5(2), 5(4), min=0, max=400}
  char	carray[5]= 5("Junk")
  bool	flags[4,-3:3] = 28(NO) {mode="h", prompt="Value set"}
  file	inp_files[3]= "fil1.inp", "fil2.inp", "fil3.inp"
  <P>
  int	karray[3]=1	# (note second and third elements are undefined)
  struct	*list="inputfile.list" {mode="q"}
  int	*ilist="infile.inp" {mode="h", min=0, max=100}
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  <PRE>
  Options are only permitted for parameters, not local variables.
  The filetype options are recognized but are not implemented internally.
  </PRE>
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  parameters, procedure
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SYNTAX' 'ELEMENTS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
