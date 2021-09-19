.. _nhedit:

nhedit: Edit image header using a command file
==============================================

**Package: imutil**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  nhedit - edit or view an image header interactively or using a command file
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <pre>
  nhedit images fields value comment
  </pre>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>images</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='images' Line='images' -->
  <dd>Template specifying the images to be edited.
  </dd>
  </dl>
  <dl>
  <dt><b>fields</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='fields' Line='fields' -->
  <dd>Template specifying the fields to be edited in each image.  The template is
  expanded independently for each image against the set of all fields in the
  image header. Special values for fields includes 'default_pars' that works only
  with a command file; 'add_blank' to add a blank field value with a string as 
  value; 'add_textf' to add a text file content to the header. See description
  for more details.
  </dd>
  </dl>
  <dl>
  <dt><b>value</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='value' Line='value' -->
  <dd>Either a string constant or a general expression (if the first character is
  a left parenthesis) to be evaluated to compute the new value of each field.
  With the rename switch the value is the new field name (keyword).
  A single expression is used for all fields.  The special value <tt>"."</tt> causes the
  value of each field to be printed rather than edited.
  </dd>
  </dl>
  <dl>
  <dt><b>comment</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='comment' Line='comment' -->
  <dd>String constant for the comment section of the header card. This value will 
  replace the existing comment of a header or clear it if is empty (<tt>""</tt>).
  The special value <tt>"."</tt> causes the field to be printed rather than edited.
  </dd>
  </dl>
  <dl>
  <dt><b>comfile = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='comfile' Line='comfile = ""' -->
  <dd>Alternate command file. If specified, the <i>fields</i>, <i>value</i>, and 
  <i>comment</i> parameters are ignored and commands are taken from the named
  file.  See below for a detailed discussion and examples.
  </dd>
  </dl>
  <dl>
  <dt><b>after = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='after' Line='after = ""' -->
  <dd>Insert the new field after the named <tt>"pivot keyword"</tt>.   If this keyword
  does not exist in the header, the new keyword is added to the end of the 
  image header.
  </dd>
  </dl>
  <dl>
  <dt><b>before = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='before' Line='before = ""' -->
  <dd>Insert the new field before the named <tt>"pivot keyword"</tt>. If this keyword 
  does not exist in the header, the new keyword is added to the end of the 
  image header.
  </dd>
  </dl>
  <dl>
  <dt><b>add = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='add' Line='add = no' -->
  <dd>Change the operation of the editor from update to add new field. If the
  field already exists it is edited.  If this option is selected the field
  list may name only a single field. The add switch takes precedence
  over the addonly, delete, and rename switches.
  </dd>
  </dl>
  <dl>
  <dt><b>addonly = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='addonly' Line='addonly = no' -->
  <dd>Change the operation of the editor from update to add a new field. If the
  field already exists it is not changed.  If this option is selected the field
  list may name only a single field. The addonly switch takes precedence over
  the delete and rename switches.
  </dd>
  </dl>
  <dl>
  <dt><b>delete = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='delete' Line='delete = no' -->
  <dd>Change the operation of the editor from update to delete field.
  The listed fields are deleted from each image.  This takes precedence
  or the rename switch.
  </dd>
  </dl>
  <dl>
  <dt><b>rename = no</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='rename' Line='rename = no' -->
  <dd>Change the operation of the editor from update field to rename field.
  The listed fields are renamed in each image if they exist.  The value
  is parameter specifies the new keyword name.  There is
  no error if the field does not exist.  The comment value is ignored
  since this operation only affects the field name.
  </dd>
  </dl>
  <dl>
  <dt><b>verify = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='verify' Line='verify = yes' -->
  <dd>Interactively verify all operations which modify the image database.
  The editor will describe the operation to be performed, prompting with the
  new value of the parameter in the case of a field edit.  Type carriage
  return or <tt>"yes"</tt> to complete the operation, or enter a new value explicitly
  as a string.  Respond with <tt>"no"</tt> if you do not wish to change the value of
  the parameter.
  </dd>
  </dl>
  <dl>
  <dt><b>show = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='show' Line='show = yes' -->
  <dd>Print a record of each operation which modifies the database upon the standard
  output.  Old values are given as well as new values, making it possible to
  undo an edit operation.
  </dd>
  </dl>
  <dl>
  <dt><b>update = yes</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='update' Line='update = yes' -->
  <dd>Enable updating of the image database.  If updating is disabled the edit
  operations are performed in memory but image headers will not be updated
  on disk.
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  1. Basic Usage
  </p>
  <p>
      The most basic functions of the image header editor are modification and
  inspection of the fields of an image header.  Both the <tt>"standard"</tt> and
  <tt>"user"</tt> fields may be edited in the same fashion, although not all standard
  fields are writable.  For example, to change the value of the standard field
  <tt>"title"</tt> of the image <tt>"m74"</tt> to <tt>"sky flat"</tt> and enter a comment  field we
  would enter the following command.
  </p>
  <p>
  	cl&gt; nhedit m74 title <tt>"sky flat"</tt> <tt>"comment field"</tt>
  </p>
  <p>
  If <i>verify</i> mode is selected the editor will print the old value of the
  field and query with the new value, allowing some other value to be entered
  instead, e.g.:
  </p>
  <pre>
  	cl&gt; nhedit m74 title "sky flat" "comment field"
  	m74,i_title ("old title" -&gt; "sky flat"):
  </pre>
  <p>
  To accept the new value shown to the right of the arrow, type carriage
  return or <tt>"yes"</tt> or <tt>"y"</tt> followed by carriage return.  To continue without
  changing the value of the field in question enter <tt>"no"</tt> or <tt>"n"</tt> followed by
  carriage return.  To enter some other value merely type in the new value.
  If the new value is one of the reserved strings, e.g., <tt>"yes"</tt> or <tt>"no"</tt>,
  enter it preceded by a backslash.  If verification is enabled you will
  also be asked if you want to update the header, once all header fields
  have been edited.  This is your last chance to change your mind before
  the header is modified on disk.  If you respond negatively the image header
  will not be updated, and editing will continue with the next image.
  If the response is <tt>"q"</tt> the editor will exit entirely.
  </p>
  <p>
  To conveniently print the value of the field <tt>"title"</tt> without modifying 
  the image header, we repeat the command with the special value <tt>"."</tt> and <tt>"."</tt> 
  for the comment portion.
  </p>
  <p>
  	cl&gt; nhedit m74 title . .
  </p>
  <p>
  To print (or edit) the values of all header fields a field template may be
  given.
  </p>
  <p>
  	cl&gt; nhedit m74 * . . 
  </p>
  <p>
  To print (or edit) the values of only a few fields the field template may
  be given as a list.
  </p>
  <p>
  	cl&gt; nhedit m74 w0,wpc . .
  </p>
  <p>
  To print the value of one or more fields in a set of images, an image template
  may be given.  Both image templates and field templates may be given if
  desired.
  </p>
  <p>
  	cl&gt; nhedit n1.* exp . .
  </p>
  <p>
  Abbreviations are not permitted for field names, i.e., the given template
  must match the full field name.  Currently, field name matches are case
  insensitive since image headers are often converted to and from FITS headers,
  which are case insensitive.
  </p>
  <p>
  2. Advanced Usage
  </p>
  <p>
      The header editor is capable of performing global edits on entire image
  databases wherein the new value of each field is computed automatically at
  edit time and may depend on the values of other fields in the image header.
  Editing may be performed in either batch or interactive mode.  An audit trail
  may be maintained (via the <i>show</i> switch and i/o redirection), permitting
  restoration of the database in the event of an error.  Trial runs may be made
  with updating disabled, before committing to an actual edit which modifies the
  database.
  </p>
  <p>
  The major editing functions of the <i>nhedit</i> task are the following:
  </p>
  <pre>
  	update		modify the value of a field or fields
  	addonly		add a new field
  	add		add a new field or modify an old one
  	delete		delete a set of fields
  	rename		rename a set of fields
  </pre>
  <p>
  In addition, <i>nhedit</i> may be used merely to inspect the values of the header
  fields, without modification of the image database.
  </p>
  <p>
  2.1 Special header fields
  </p>
  <pre>
      add_blank		Add blank keyword field with optional comment
               ex: nhedit add_blank "    this is a comment with no kw"
      add_textf		Add the content of a text file into the header
               ex: nhedit add_textf "my_text.txt" add+
  </pre>
  <p>
  All keyword addition can be inserted after or before an existent keyword; use
  the 'after' and 'before' parameter.
  </p>
  <p>
  2.2 Input commands from a command file.
  </p>
  <p>
  All header editing command can be put together in a text file and run it as:
  </p>
  <p>
  nhedit file*.fits comfile=command_file.txt
  </p>
  <p>
  2.3 Standard header fields
  </p>
  <p>
      The header editor may be used to access both the standard image header
  fields and any user or application defined fields.  The standard header fields
  currently defined are shown below.  There is no guarantee that the names and/or
  usage of these fields will not change in the future.
  </p>
  <pre>
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
  </pre>
  <p>
  The standard header field names have an <tt>"i_"</tt> prefix to reduce the possibility
  of a name collision with a user field name, and to distinguish the two classes
  of parameters in templates.  The prefix may be omitted provided the simple
  name is unique.
  </p>
  <p>
  2.4 Field name template
  </p>
  <p>
      The form of the field name list or template parameter <i>fields</i> is
  equivalent to that of a filename template except that <tt>"@listfile"</tt> is not
  supported, and of course the template is expanded upon the field name list
  of an image, rather than upon a directory.  Abbreviations are not permitted
  in field names and case is not significant.  Case is ignored in this context
  due to the present internal storage format for the user parameters (FITS),
  which also limits the length of a user field name to 8 characters.
  </p>
  <p>
  2.5 Value expression
  </p>
  <p>
      The <i>value</i> parameter is a string type parameter.  If the first
  character in the string is a left parenthesis the string is interpreted as
  an algebraic expression wherein the operands may be constants, image header
  variables (field names), special variables (defined below), or calls to
  intrinsic functions.  The expression syntax is equivalent to that used in
  the CL and SPP languages.  If the value string is not parenthesized it is
  assumed to be a string constant.  The <i>value</i> string will often contain
  blanks, quotes, parenthesis, etc., and hence must usually be quoted to avoid
  interpretation by the CL rather than by the header editor.
  </p>
  <p>
  For example, the command
  </p>
  <p>
  	cl&gt; nhedit m74 title <tt>"title // ';ss'"</tt> <tt>"."</tt>
  </p>
  <p>
  would change the title to the literal string constant <tt>"title // ';ss'"</tt>,
  whereas the command
  </p>
  <p>
  	cl&gt; nhedit m74 title <tt>"(title // ';ss')"</tt> <tt>"."</tt>
  </p>
  <p>
  would concatenate the string <tt>";ss"</tt> to the old title string.  We require
  parenthesis for expression evaluation to avoid the need to doubly quote
  simple string constant values, which would be even more confusing for the
  user than using parenthesis.  For example, if expressions did not have to
  be parenthesized, the first example in the basic usage section would have
  to be entered as shown below.
  </p>
  <p>
  	cl&gt; nhedit m74 title '<tt>"sky flat"</tt>'	# invalid command
  </p>
  <p>
  Expression evaluation for <i>nhedit</i>, <i>hselect</i>, and similar tasks
  is carried out internally by the FMTIO library routine <b>evexpr</b>.
  For completeness minimal documentation is given here, but the documentation
  for <i>evexpr</i> itself should be consulted if additional detail is required
  or if problems occur.
  </p>
  <p>
  2.5.1 operators
  </p>
  <p>
      The following operators are recognized in value expressions.  With the
  exception of the operators <tt>"?"</tt>, <tt>"?="</tt>, and <tt>"@"</tt>, the operator set is equivalent
  to that available in the CL and SPP languages.
  </p>
  <pre>
  	+  -  *  /		arithmetic operators
  	**			exponentiation
  	//			string concatenation
  	!  -			boolean not, unary negation
  	&lt;  &lt;= &gt;  &gt;=		order comparison (works for strings)
  	== != &amp;&amp; ||		equals, not equals, and, or
  	?=			string equals pattern
  	? :			conditional expression
  	@			reference a variable
  </pre>
  <p>
  The operators <tt>"=="</tt>, <tt>"&amp;&amp;"</tt>, and <tt>"||"</tt> may be abbreviated as <tt>"="</tt>, <tt>"&amp;"</tt>, and <tt>"|"</tt>
  if desired.  The ?= operator performs pattern matching upon strings.
  For example, the boolean expression shown below will be true whenever the
  field <tt>"title"</tt> contains the substring <tt>"sky"</tt>.
  </p>
  <p>
  	(title ?= '*sky*')
  </p>
  <p>
  The conditional expression operator <tt>'?'</tt>, which is patterned after a similar
  operator in C, is used to make IF ELSE like decisions within an expression.
  The syntax is as follows:
  </p>
  <p>
  	&lt;bool_expr&gt; <tt>'?'</tt> &lt;true_expr&gt; <tt>':'</tt> &lt;false_expr&gt; 
  </p>
  <p>
  e.g., the expression
  </p>
  <p>
  	((a &gt; b) ? 1 : 0)
  </p>
  <p>
  has the value 1 if A is greater than B, and 0 otherwise.  The datatypes
  of the true and false expressions need not be the same, unlike a compiled
  language.  Note that if the parenthesis are omitted ambiguous forms of
  the expression are possible, e.g.:
  </p>
  <p>
  	(a &gt; b) ? 1 : a + 1
  </p>
  <p>
  could be interpreted either as
  </p>
  <p>
  	((a &gt; b) ? 1 : a) + 1
  or as
  	(a &gt; b) ? 1 : (a + 1)
  </p>
  <p>
  If the parenthesis are omitted the latter interpretation is assumed.
  </p>
  <p>
  The operator @ must be used to dereference variables that have names with
  funny (nonalphanumeric) characters in them, forcing the variable name to
  be given as a string constant.  For example, the value of the expression
  </p>
  <p>
  	@<tt>"co-flag"</tt>
  </p>
  <p>
  is the value of the variable <tt>"co-flag"</tt>.  If the variable were referenced
  directly by name the <tt>"-"</tt> would be interpreted as the subtraction operator,
  causing an unknown variable reference (e.g., to <tt>"co"</tt>).
  The operand following the @ may be any string valued expression.
  The @ operator is right associative, hence the construct <tt>"@@param"</tt> is the
  value of the parameter named by the value of the parameter <tt>"param"</tt>.
  </p>
  <p>
  An expression may contain operands of datatypes bool, int, real, and string.
  Mixed mode expressions are permitted with automatic type coercion.  Most type
  coercions from boolean or string to other datatypes are illegal.  The boolean
  constants <tt>"yes"</tt> and <tt>"no"</tt> are predefined and may be used within expressions.
  </p>
  <p>
  2.5.2 intrinsic functions
  </p>
  <p>
      A number of standard intrinsic functions are recognized within expressions.
  The set of functions currently supported is shown below.
  </p>
  <pre>
  	abs	acos	asin	atan	atan2	bool	cos
  	exp	int	log	log10	max	min	mod
  	nint	real	sin	sqrt	str	tan	
  </pre>
  <p>
  The trigonometric functions operate in units of degrees rather than radians.
  The <i>min</i> and <i>max</i> functions may have any number of arguments up
  to a maximum of sixteen or so (configurable).  The arguments need not all
  be of the same datatype.
  </p>
  <p>
  A function call may take either of the following forms:
  </p>
  <pre>
  	&lt;identifier&gt; <tt>'('</tt> arglist <tt>')'</tt>
  or
  	&lt;string_expr&gt; <tt>'('</tt> arglist <tt>')'</tt>
  </pre>
  <p>
  The first form is the conventional form found in all programming languages.
  The second permits the generation of function names by string valued
  expressions and might be useful on rare occasions.
  </p>
  <p>
  2.5.3 special operands
  </p>
  <p>
      As noted earlier, expression operands may be constants, variables (header
  fields), function calls, or references to any of the special variables.
  The following special variables are recognized within expressions:
  </p>
  <pre>
  	.		A string constant, used to flag printing
  	$		The value of the "current field"
  	$F		The name of the "current field"
  	$I		The name of the "current image"
  	$T		The current clock time (an integer value)
  </pre>
  <p>
  These builtin variables are especially useful for constructing context
  dependent expressions.  For example, the value of a field may be incremented
  by 100 by assigning it the value <tt>"$ + 100"</tt>.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. Globally edit the database <tt>"n1"</tt>, setting the value of the string parameter
  <tt>"obs"</tt> to <tt>"sky"</tt> if <tt>"s-flag"</tt> is 1, to <tt>"obj"</tt> otherwise.
  </p>
  <p>
      cl&gt; nhedit n1.* obs '(@<tt>"s-flag"</tt> == 1 ? <tt>"sky"</tt> : <tt>"obj"</tt>)' <tt>"Observation value"</tt>
  </p>
  <p>
  2. Globally edit the same database, replacing the value of the parameter
  <tt>"variance"</tt> by the square root of the original value.
  </p>
  <p>
      cl&gt; nhedit n1.* var '(sqrt(var))' <tt>"Variance value"</tt>
  </p>
  <p>
  3. Replace the values of the fields A and B by the absolute value of the
  original value:
  </p>
  <p>
      cl&gt; nhedit n1.* a,b '(abs($))<tt>' '</tt>Absolute value'
  </p>
  <p>
  4. Add a blank field with a comment after a given field (K5DX).
  </p>
  <p>
      cl&gt; nhedit file.fits add_blank <tt>"INSTRUMENT DESCRIPTION "</tt> after=k5dx add+
    
      Notice the use of the special field value 'add_blank' which will be 
  replaced by a blank keyword in the header.
  </p>
  <p>
  5. Add HISTORY card before a given keyword
  </p>
  <pre>
     cl&gt; nhedit file.fits history \<br>
         "History text from column 9 to 80, no quotes" before=wcsdim add+
  
  </pre>
  <p>
  6. Run a command file through the first 50 extensions
  </p>
  <pre>
  
      cl&gt;  for(i=1;i&lt;51;i=i+1) {
            nhedit("mymef["//i//"]",comfile="home$hh.in")
         }
  
  </pre>
  <p>
  7. Add a text file to the header. This will be put as HISTORY lines with 
  text appropriately split when long lines are encountered. Start putting the
  text after the keyword KEYWN.
  </p>
  <pre>
  
     cl&gt; nhedit add_textf "mytext_file.tx" after=KEYWN add+
  
  
  </pre>
  <p>
  8. Run nhedit through all the extensions in a MEF file. Assuming it is 6, then:
  </p>
  <pre>
  
     cl&gt; for(i=1;i&lt;7;i=i+1)
            nhedit("mymef.fits["//i//"]",comfi="home$myheader.txt")
  
  </pre>
  <p>
  9. Run several fits files with the same set of header commands from the file
  <tt>"hdrc.txt"</tt>.
  </p>
  <p>
     cl&gt; nhedit file*.fits commfile=hdrc.txt
  </p>
  <p>
  As an example the 'hdrc.txt' content can be: (Notice the 'default_pars' command)
  </p>
  <pre>
  # 
  # Sample command file for nhedit task.
  #
  # Establish the default parameters for the rest of the commands.
  
  default_pars upda+ add+ show- veri-
  
  # Notice the use of commas if you desire.
  "DETECTOR" 'Newfirm', "comment string"
  ONELE <tt>'A'</tt> "comment to A"
  # 
  # Now delete a keyword
  ONELE1 del+ show+
  add_blank  "    /blank keyw"
  
  # add a boolean value T
  ONELE1 '(1==1)', "comment to A"
  
     "DETSIZE", '[1:2048,1:2048]'
     "ENVTEM", 1.5600000000000E+01
  
  # Add a field with string value <tt>'T'</tt>
  ONELEi2 <tt>'T'</tt>
  
  bafkeyw1 123.456 "comment to key1" before="WCSDIM" addonly+  show-
  add_blank    "COMMENT FOR A BLANK"  after="FR-SCALE" add+  show-
  history "this is a hist to append"  add+ show-
  history "this is a hist 22 after trim pkey"  after="TRIM" add+ show-
  comment "this is a comment" after="FR-SCALE" add+ show-
  # END OF HDRC.TXT FILE
  
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  hselect, hedit, mkheader, imgets, imheader
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  -->
  
