.. _hselect:

hselect — Select a subset of images satisfying a boolean expression
===================================================================

**Package: imutil**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  hselect - extract keyword values from images satisfying a selection expression
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  hselect images fields expr
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>images</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>Images forming the set from which selected images are to be drawn.
  </DD>
  </DL>
  <DL>
  <DT><B>fields</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='fields' Line='fields'>
  <DD>Comma separated list of keywords or keyword patterns to be extracted
  from each selected image.  The list elements are matched against the
  set of keywords in the header except for those beginning with "<TT>$</TT>" which
  are special values or explicit checks for keywords that might be missing.
  </DD>
  </DL>
  <DL>
  <DT><B>expr</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='expr' Line='expr'>
  <DD>The boolean expression to be used as the selection criteria.  The expression
  is evaluated independently for each image.
  </DD>
  </DL>
  <DL>
  <DT><B>missing = "<TT>INDEF</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='missing' Line='missing = "INDEF"'>
  <DD>Output value for missing keywords.  Note that this will only occur when the
  fields are specified with leading "<TT>$</TT>".
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The function of <I>hselect</I> is to extract keyword values from a subset
  of images satisfying a boolean selection expression.  The resultant table
  of keyword values is output in list form, suitable for further analysis
  or for use to generate a list of images to be processed by another task.
  <P>
  The form of the boolean expression <I>expr</I> is fully documented in the
  manual page for the <I>hedit</I> task.  In the case of <I>hselect</I> task,
  however, the expression need not be parenthesized to be evaluated as an
  expression.
  <P>
  The keywords whose values are to be output are specified by the <I>fields</I>
  parameter.  This is a comma delimited list of keywords and patterns.  The
  keywords and patterns are matched against the set of keywords in the image.
  Of particular importance is that explicit keywords, that is without any
  wildcard, are matched against the header and so if the keyword is not in the
  header then the keyword value is not output.  If one wants to explicitly
  output a place holder for a missing keyword use a leading $; e.g. $mykey.
  If the keyword is absent then the value given by the <I>missing</I>
  parameter will be output.  This is useful when scanning the output.
  <P>
  In addition to escaping the keyword matching, the leading $ character is
  also used to select special values such as "<TT>$I</TT>" for the name of the current
  image.  See <B>hedit</B> for more on the special values and pattern syntax.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Compute the mean exposure time for all the images in a database.  Note that
  the argument "<TT>yes</TT>" is a trivial case of a general boolean expression and
  hence need not be quoted.
  <P>
  	cl&gt; hselect n1.* exp yes | average
  <P>
  2. Print the name, length of axes 1 and 2, and title of all two dimensional
  images in a database.
  <P>
  <P>
  <PRE>
  	cl&gt; hselect n1.* $I,naxis[12],title 'naxis == 2'
  	n1.0001	512	512	quartz
  	n1.0002 512	512	"dome flat"
  	n1.0005 384	800	"ngc 3127 at 45 degrees"
  	cl&gt;
  </PRE>
  <P>
  <P>
  3. Produce an image name list for use to drive another task.  The selection
  criterion is all images for which the value of the parameter "<TT>q-flag</TT>"
  has the value 1.  Note carefully the use of quotes.  If the @ operator
  is unfamiliar read the manual page for <I>hedit</I>.
  <P>
  	cl&gt; hselect n1.* $I '@"<TT>q-flag</TT>" == 1' &gt; imlist
  <P>
  If the parameter "<TT>q-flag</TT>" were instead named "<TT>qflag</TT>", the following
  simpler expression would suffice.
  <P>
  	cl&gt; hselect n1.* $I 'qflag == 1' &gt; imlist
  <P>
  4.  Scan a set of keyword and allow for missing keywords.
  <P>
  <PRE>
  	cl&gt; hselect pix $I,$exptime,$airmass yes missing=INDEF |
  	&gt;&gt;&gt; scan (s1, x, y)
  </PRE>
  <P>
  Note that when checking for missing values the missing value must be
  of the appropriate type or else you need to use string variables or
  nscan to check.  The default missing value is "<TT>INDEF</TT>" which can be
  scanned into both string and numerical variables.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Since individual image headers are currently stored as separate files,
  selection from a large database is quite slow.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  hedit, imgets, imheader
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
