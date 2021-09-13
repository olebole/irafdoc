.. _nhedit:

nhedit — Edit image header using a command file
===============================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  nhedit - edit or view an image header interactively or using a command file
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  <PRE>
  nhedit images fields value comment
  </PRE>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Template specifying the images to be edited.
  </DD>
  </DL>
  <DL>
  <DT><B>fields</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fields' Line='fields'>
  <DD>Template specifying the fields to be edited in each image.  The template is
  expanded independently for each image against the set of all fields in the
  image header. Special values for fields includes 'default_pars' that works only
  with a command file; 'add_blank' to add a blank field value with a string as 
  value; 'add_textf' to add a text file content to the header. See description
  for more details.
  </DD>
  </DL>
  <DL>
  <DT><B>value</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='value' Line='value'>
  <DD>Either a string constant or a general expression (if the first character is
  a left parenthesis) to be evaluated to compute the new value of each field.
  With the rename switch the value is the new field name (keyword).
  A single expression is used for all fields.  The special value "<TT>.</TT>" causes the
  value of each field to be printed rather than edited.
  </DD>
  </DL>
  <DL>
  <DT><B>comment</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='comment' Line='comment'>
  <DD>String constant for the comment section of the header card. This value will 
  replace the existing comment of a header or clear it if is empty ("<TT></TT>").
  The special value "<TT>.</TT>" causes the field to be printed rather than edited.
  </DD>
  </DL>
  <DL>
  <DT><B>comfile = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='comfile' Line='comfile = ""'>
  <DD>Alternate command file. If specified, the <I>fields</I>, <I>value</I>, and 
  <I>comment</I> parameters are ignored and commands are taken from the named
  file.  See below for a detailed discussion and examples.
  </DD>
  </DL>
  <DL>
  <DT><B>after = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='after' Line='after = ""'>
  <DD>Insert the new field after the named "<TT>pivot keyword</TT>".   If this keyword
  does not exist in the header, the new keyword is added to the end of the 
  image header.
  </DD>
  </DL>
  <DL>
  <DT><B>before = "<TT></TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='before' Line='before = ""'>
  <DD>Insert the new field before the named "<TT>pivot keyword</TT>". If this keyword 
  does not exist in the header, the new keyword is added to the end of the 
  image header.
  </DD>
  </DL>
  <DL>
  <DT><B>add = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='add' Line='add = no'>
  <DD>Change the operation of the editor from update to add new field. If the
  field already exists it is edited.  If this option is selected the field
  list may name only a single field. The add switch takes precedence
  over the addonly, delete, and rename switches.
  </DD>
  </DL>
  <DL>
  <DT><B>addonly = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='addonly' Line='addonly = no'>
  <DD>Change the operation of the editor from update to add a new field. If the
  field already exists it is not changed.  If this option is selected the field
  list may name only a single field. The addonly switch takes precedence over
  the delete and rename switches.
  </DD>
  </DL>
  <DL>
  <DT><B>delete = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='delete' Line='delete = no'>
  <DD>Change the operation of the editor from update to delete field.
  The listed fields are deleted from each image.  This takes precedence
  or the rename switch.
  </DD>
  </DL>
  <DL>
  <DT><B>rename = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='rename' Line='rename = no'>
  <DD>Change the operation of the editor from update field to rename field.
  The listed fields are renamed in each image if they exist.  The value
  is parameter specifies the new keyword name.  There is
  no error if the field does not exist.  The comment value is ignored
  since this operation only affects the field name.
  </DD>
  </DL>
  <DL>
  <DT><B>verify = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='verify' Line='verify = yes'>
  <DD>Interactively verify all operations which modify the image database.
  The editor will describe the operation to be performed, prompting with the
  new value of the parameter in the case of a field edit.  Type carriage
  return or "<TT>yes</TT>" to complete the operation, or enter a new value explicitly
  as a string.  Respond with "<TT>no</TT>" if you do not wish to change the value of
  the parameter.
  </DD>
  </DL>
  <DL>
  <DT><B>show = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='show' Line='show = yes'>
  <DD>Print a record of each operation which modifies the database upon the standard
  output.  Old values are given as well as new values, making it possible to
  undo an edit operation.
  </DD>
  </DL>
  <DL>
  <DT><B>update = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='update' Line='update = yes'>
  <DD>Enable updating of the image database.  If updating is disabled the edit
  operations are performed in memory but image headers will not be updated
  on disk.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  1. Basic Usage
  <P>
      The most basic functions of the image header editor are modification and
  inspection of the fields of an image header.  Both the "<TT>standard</TT>" and
  "<TT>user</TT>" fields may be edited in the same fashion, although not all standard
  fields are writable.  For example, to change the value of the standard field
  "<TT>title</TT>" of the image "<TT>m74</TT>" to "<TT>sky flat</TT>" and enter a comment  field we
  would enter the following command.
  <P>
  	cl&gt; nhedit m74 title "<TT>sky flat</TT>" "<TT>comment field</TT>"
  <P>
  If <I>verify</I> mode is selected the editor will print the old value of the
  field and query with the new value, allowing some other value to be entered
  instead, e.g.:
  <P>
  <PRE>
  	cl&gt; nhedit m74 title "sky flat" "comment field"
  	m74,i_title ("old title" -&gt; "sky flat"):
  </PRE>
  <P>
  To accept the new value shown to the right of the arrow, type carriage
  return or "<TT>yes</TT>" or "<TT>y</TT>" followed by carriage return.  To continue without
  changing the value of the field in question enter "<TT>no</TT>" or "<TT>n</TT>" followed by
  carriage return.  To enter some other value merely type in the new value.
  If the new value is one of the reserved strings, e.g., "<TT>yes</TT>" or "<TT>no</TT>",
  enter it preceded by a backslash.  If verification is enabled you will
  also be asked if you want to update the header, once all header fields
  have been edited.  This is your last chance to change your mind before
  the header is modified on disk.  If you respond negatively the image header
  will not be updated, and editing will continue with the next image.
  If the response is "<TT>q</TT>" the editor will exit entirely.
  <P>
  To conveniently print the value of the field "<TT>title</TT>" without modifying 
  the image header, we repeat the command with the special value "<TT>.</TT>" and "<TT>.</TT>" 
  for the comment portion.
  <P>
  	cl&gt; nhedit m74 title . .
  <P>
  To print (or edit) the values of all header fields a field template may be
  given.
  <P>
  	cl&gt; nhedit m74 * . . 
  <P>
  To print (or edit) the values of only a few fields the field template may
  be given as a list.
  <P>
  	cl&gt; nhedit m74 w0,wpc . .
  <P>
  To print the value of one or more fields in a set of images, an image template
  may be given.  Both image templates and field templates may be given if
  desired.
  <P>
  	cl&gt; nhedit n1.* exp . .
  <P>
  Abbreviations are not permitted for field names, i.e., the given template
  must match the full field name.  Currently, field name matches are case
  insensitive since image headers are often converted to and from FITS headers,
  which are case insensitive.
  <P>
  <P>
  2. Advanced Usage
  <P>
      The header editor is capable of performing global edits on entire image
  databases wherein the new value of each field is computed automatically at
  edit time and may depend on the values of other fields in the image header.
  Editing may be performed in either batch or interactive mode.  An audit trail
  may be maintained (via the <I>show</I> switch and i/o redirection), permitting
  restoration of the database in the event of an error.  Trial runs may be made
  with updating disabled, before committing to an actual edit which modifies the
  database.
  <P>
  The major editing functions of the <I>nhedit</I> task are the following:
  <P>
  <PRE>
  	update		modify the value of a field or fields
  	addonly		add a new field
  	add		add a new field or modify an old one
  	delete		delete a set of fields
  	rename		rename a set of fields
  </PRE>
  <P>
  In addition, <I>nhedit</I> may be used merely to inspect the values of the header
  fields, without modification of the image database.
  <P>
  2.1 Special header fields
  <P>
  <PRE>
  <PRE>
      add_blank		Add blank keyword field with optional comment
               ex: nhedit add_blank "    this is a comment with no kw"
      add_textf		Add the content of a text file into the header
               ex: nhedit add_textf "my_text.txt" add+
  </PRE>
  </PRE>
  <P>
  All keyword addition can be inserted after or before an existent keyword; use
  the 'after' and 'before' parameter.
  <P>
  2.2 Input commands from a command file.
  <P>
  All header editing command can be put together in a text file and run it as:
  <P>
  nhedit file*.fits comfile=command_file.txt
  <P>
  2.3 Standard header fields
  <P>
      The header editor may be used to access both the standard image header
  fields and any user or application defined fields.  The standard header fields
  currently defined are shown below.  There is no guarantee that the names and/or
  usage of these fields will not change in the future.
  <P>
  <P>
  <PRE>
  <PRE>
  	i_ctime		int		create time
  	i_history	string		history comments
  	i_limtime	int		time when min,max last updated
  	i_maxpixval	real		maximum pixel value
  	i_minpixval	real		minimum pixel value
  	i_mtime		int		time of last modify
  	i_naxis		int		number of axes (dimensionality)
  	i_naxis[1-7]	int		length of each axis
  	i_pixfile	string		pathname of pixel storage file
  	i_pixtype	int		pixel datatype code
  	i_title		string		title string
  </PRE>
  </PRE>
  <P>
  <P>
  The standard header field names have an "<TT>i_</TT>" prefix to reduce the possibility
  of a name collision with a user field name, and to distinguish the two classes
  of parameters in templates.  The prefix may be omitted provided the simple
  name is unique.
  <P>
  <P>
  2.4 Field name template
  <P>
      The form of the field name list or template parameter <I>fields</I> is
  equivalent to that of a filename template except that "<TT>@listfile</TT>" is not
  supported, and of course the template is expanded upon the field name list
  of an image, rather than upon a directory.  Abbreviations are not permitted
  in field names and case is not significant.  Case is ignored in this context
  due to the present internal storage format for the user parameters (FITS),
  which also limits the length of a user field name to 8 characters.
  <P>
  <P>
  2.5 Value expression
  <P>
      The <I>value</I> parameter is a string type parameter.  If the first
  character in the string is a left parenthesis the string is interpreted as
  an algebraic expression wherein the operands may be constants, image header
  variables (field names), special variables (defined below), or calls to
  intrinsic functions.  The expression syntax is equivalent to that used in
  the CL and SPP languages.  If the value string is not parenthesized it is
  assumed to be a string constant.  The <I>value</I> string will often contain
  blanks, quotes, parenthesis, etc., and hence must usually be quoted to avoid
  interpretation by the CL rather than by the header editor.
  <P>
  For example, the command
  <P>
  	cl&gt; nhedit m74 title "<TT>title // ';ss'</TT>" "<TT>.</TT>"
  <P>
  would change the title to the literal string constant "<TT>title // ';ss'</TT>",
  whereas the command
  <P>
  	cl&gt; nhedit m74 title "<TT>(title // ';ss')</TT>" "<TT>.</TT>"
  <P>
  would concatenate the string "<TT>;ss</TT>" to the old title string.  We require
  parenthesis for expression evaluation to avoid the need to doubly quote
  simple string constant values, which would be even more confusing for the
  user than using parenthesis.  For example, if expressions did not have to
  be parenthesized, the first example in the basic usage section would have
  to be entered as shown below.
  <P>
  	cl&gt; nhedit m74 title '"<TT>sky flat</TT>"'	# invalid command
  <P>
  Expression evaluation for <I>nhedit</I>, <I>hselect</I>, and similar tasks
  is carried out internally by the FMTIO library routine <B>evexpr</B>.
  For completeness minimal documentation is given here, but the documentation
  for <I>evexpr</I> itself should be consulted if additional detail is required
  or if problems occur.
  <P>
  <P>
  2.5.1 operators
  <P>
      The following operators are recognized in value expressions.  With the
  exception of the operators "<TT>?</TT>", "<TT>?=</TT>", and "<TT>@</TT>", the operator set is equivalent
  to that available in the CL and SPP languages.
  <P>
  <P>
  <PRE>
  	+  -  *  /		arithmetic operators
  	**			exponentiation
  	//			string concatenation
  	!  -			boolean not, unary negation
  	&lt;  &lt;= &gt;  &gt;=		order comparison (works for strings)
  	== != &amp;&amp; ||		equals, not equals, and, or
  	?=			string equals pattern
  	? :			conditional expression
  	@			reference a variable
  </PRE>
  <P>
  <P>
  The operators "<TT>==</TT>", "<TT>&amp;&amp;</TT>", and "<TT>||</TT>" may be abbreviated as "<TT>=</TT>", "<TT>&amp;</TT>", and "<TT>|</TT>"
  if desired.  The ?= operator performs pattern matching upon strings.
  For example, the boolean expression shown below will be true whenever the
  field "<TT>title</TT>" contains the substring "<TT>sky</TT>".
  <P>
  	(title ?= '*sky*')
  <P>
  The conditional expression operator <TT>'?'</TT>, which is patterned after a similar
  operator in C, is used to make IF ELSE like decisions within an expression.
  The syntax is as follows:
  <P>
  	&lt;bool_expr&gt; <TT>'?'</TT> &lt;true_expr&gt; <TT>':'</TT> &lt;false_expr&gt; 
  <P>
  e.g., the expression
  <P>
  	((a &gt; b) ? 1 : 0)
  <P>
  has the value 1 if A is greater than B, and 0 otherwise.  The datatypes
  of the true and false expressions need not be the same, unlike a compiled
  language.  Note that if the parenthesis are omitted ambiguous forms of
  the expression are possible, e.g.:
  <P>
  	(a &gt; b) ? 1 : a + 1
  <P>
  could be interpreted either as
  <P>
  	((a &gt; b) ? 1 : a) + 1
  or as
  	(a &gt; b) ? 1 : (a + 1)
  <P>
  If the parenthesis are omitted the latter interpretation is assumed.
  <P>
  The operator @ must be used to dereference variables that have names with
  funny (nonalphanumeric) characters in them, forcing the variable name to
  be given as a string constant.  For example, the value of the expression
  <P>
  	@"<TT>co-flag</TT>"
  <P>
  is the value of the variable "<TT>co-flag</TT>".  If the variable were referenced
  directly by name the "<TT>-</TT>" would be interpreted as the subtraction operator,
  causing an unknown variable reference (e.g., to "<TT>co</TT>").
  The operand following the @ may be any string valued expression.
  The @ operator is right associative, hence the construct "<TT>@@param</TT>" is the
  value of the parameter named by the value of the parameter "<TT>param</TT>".
  <P>
  An expression may contain operands of datatypes bool, int, real, and string.
  Mixed mode expressions are permitted with automatic type coercion.  Most type
  coercions from boolean or string to other datatypes are illegal.  The boolean
  constants "<TT>yes</TT>" and "<TT>no</TT>" are predefined and may be used within expressions.
  <P>
  <P>
  2.5.2 intrinsic functions
  <P>
      A number of standard intrinsic functions are recognized within expressions.
  The set of functions currently supported is shown below.
  <P>
  <P>
  <PRE>
  	abs	acos	asin	atan	atan2	bool	cos
  	exp	int	log	log10	max	min	mod
  	nint	real	sin	sqrt	str	tan	
  </PRE>
  <P>
  <P>
  The trigonometric functions operate in units of degrees rather than radians.
  The <I>min</I> and <I>max</I> functions may have any number of arguments up
  to a maximum of sixteen or so (configurable).  The arguments need not all
  be of the same datatype.
  <P>
  A function call may take either of the following forms:
  <P>
  <PRE>
  	&lt;identifier&gt; <TT>'('</TT> arglist <TT>')'</TT>
  or
  	&lt;string_expr&gt; <TT>'('</TT> arglist <TT>')'</TT>
  </PRE>
  <P>
  The first form is the conventional form found in all programming languages.
  The second permits the generation of function names by string valued
  expressions and might be useful on rare occasions.
  <P>
  <P>
  2.5.3 special operands
  <P>
      As noted earlier, expression operands may be constants, variables (header
  fields), function calls, or references to any of the special variables.
  The following special variables are recognized within expressions:
  <P>
  <P>
  <PRE>
  	.		A string constant, used to flag printing
  	$		The value of the "current field"
  	$F		The name of the "current field"
  	$I		The name of the "current image"
  	$T		The current clock time (an integer value)
  </PRE>
  <P>
  <P>
  These builtin variables are especially useful for constructing context
  dependent expressions.  For example, the value of a field may be incremented
  by 100 by assigning it the value "<TT>$ + 100</TT>".
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  1. Globally edit the database "<TT>n1</TT>", setting the value of the string parameter
  "<TT>obs</TT>" to "<TT>sky</TT>" if "<TT>s-flag</TT>" is 1, to "<TT>obj</TT>" otherwise.
  <P>
      cl&gt; nhedit n1.* obs '(@"<TT>s-flag</TT>" == 1 ? "<TT>sky</TT>" : "<TT>obj</TT>")' "<TT>Observation value</TT>"
  <P>
  2. Globally edit the same database, replacing the value of the parameter
  "<TT>variance</TT>" by the square root of the original value.
  <P>
      cl&gt; nhedit n1.* var '(sqrt(var))' "<TT>Variance value</TT>"
  <P>
  3. Replace the values of the fields A and B by the absolute value of the
  original value:
  <P>
      cl&gt; nhedit n1.* a,b '(abs($))<TT>' '</TT>Absolute value'
  <P>
  4. Add a blank field with a comment after a given field (K5DX).
  <P>
      cl&gt; nhedit file.fits add_blank "<TT>INSTRUMENT DESCRIPTION </TT>" after=k5dx add+
    
      Notice the use of the special field value 'add_blank' which will be 
  replaced by a blank keyword in the header.
  <P>
  5. Add HISTORY card before a given keyword
  <P>
  <PRE>
     cl&gt; nhedit file.fits history \<BR>
         "History text from column 9 to 80, no quotes" before=wcsdim add+
  <P>
  </PRE>
  6. Run a command file through the first 50 extensions
  <PRE>
  <P>
      cl&gt;  for(i=1;i&lt;51;i=i+1) {
            nhedit("mymef["//i//"]",comfile="home$hh.in")
         }
  <P>
  </PRE>
  7. Add a text file to the header. This will be put as HISTORY lines with 
  text appropriately split when long lines are encountered. Start putting the
  text after the keyword KEYWN.
  <PRE>
  <P>
     cl&gt; nhedit add_textf "mytext_file.tx" after=KEYWN add+
  <P>
  <P>
  </PRE>
  8. Run nhedit through all the extensions in a MEF file. Assuming it is 6, then:
  <PRE>
  <P>
     cl&gt; for(i=1;i&lt;7;i=i+1)
            nhedit("mymef.fits["//i//"]",comfi="home$myheader.txt")
  <P>
  </PRE>
  9. Run several fits files with the same set of header commands from the file
  "<TT>hdrc.txt</TT>".
  <P>
     cl&gt; nhedit file*.fits commfile=hdrc.txt
  <P>
  As an example the 'hdrc.txt' content can be: (Notice the 'default_pars' command)
  <P>
  <PRE>
  # 
  # Sample command file for nhedit task.
  #
  # Establish the default parameters for the rest of the commands.
  <P>
  default_pars upda+ add+ show- veri-
  <P>
  # Notice the use of commas if you desire.
  "DETECTOR" 'Newfirm', "comment string"
  ONELE <TT>'A'</TT> "comment to A"
  # 
  # Now delete a keyword
  ONELE1 del+ show+
  add_blank  "    /blank keyw"
  <P>
  # add a boolean value T
  ONELE1 '(1==1)', "comment to A"
  <P>
     "DETSIZE", '[1:2048,1:2048]'
     "ENVTEM", 1.5600000000000E+01
  <P>
  # Add a field with string value <TT>'T'</TT>
  ONELEi2 <TT>'T'</TT>
  <P>
  bafkeyw1 123.456 "comment to key1" before="WCSDIM" addonly+  show-
  add_blank    "COMMENT FOR A BLANK"  after="FR-SCALE" add+  show-
  history "this is a hist to append"  add+ show-
  history "this is a hist 22 after trim pkey"  after="TRIM" add+ show-
  comment "this is a comment" after="FR-SCALE" add+ show-
  # END OF HDRC.TXT FILE
  <P>
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  hselect, hedit, mkheader, imgets, imheader
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
