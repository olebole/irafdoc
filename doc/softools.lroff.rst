.. _lroff:

lroff — Lroff (line-roff) text formatter
========================================

**Package: softools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  <B>lroff</B> -- line oriented text formatter
  </UL>
  <! EndSection:   'NAME'>
  <H3>Purpose</H3>
  <! BeginSection: 'PURPOSE'>
  <UL>
  <B>Lroff</B> is a simple text formatter used by the IRAF on-line Help command,
  and other utilities (MANPAGE, LIST), to format text.  
  <B>Lroff</B> style documentation text may be embedded in program source files.
  <B>lroff</B> is line oriented, rather than page oriented,
  and is implemented as a library procedure rather than as a task.
  </UL>
  <! EndSection:   'PURPOSE'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  status = lroff (input, output, left_margin, right_margin)
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>input</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='input' Line='input'>
  <DD>An integer procedure, called by <B>lroff</B> to get lines of input,
  which takes the <B>lroff</B> input buffer as an argument,
  and which returns EOF upon End of File (like GETLINE).
  Each line of input must be terminated by a newline and an EOS
  (End Of String marker).
  </DD>
  </DL>
  <DL>
  <DT><B>output</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='output' Line='output'>
  <DD>A procedure, called by <B>lroff</B> to output formatted lines of text,
  which takes the <B>lroff</B> output buffer as an argument ("<TT>output (buffer)</TT>").
  </DD>
  </DL>
  <DL>
  <DT><B>left_margin</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='left_margin' Line='left_margin'>
  <DD>The first column to be filled (&gt;= 1).
  </DD>
  </DL>
  <DL>
  <DT><B>right_margin</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='right_margin' Line='right_margin'>
  <DD>The last column to be filled.
  </DD>
  </DL>
  <DL>
  <DT><B>status</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='status' Line='status'>
  <DD>ERR is returned if meaningless margins are specified, or if an unrecoverable
  error occurs during processing.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Lroff</B> input may be bracketed by "<TT>.help</TT>" and "<TT>.endhelp</TT>" directives in
  the actual source file of the program being documented (if intended as input
  to the <B>help</B> utility), or may be in a separate file.
  The input text consists
  of a mixture of lines of text and <B>lroff</B> directives.
  <B>Lroff</B> recognizes only a few directives,
  summarized in the "<TT>Request Summary</TT>" below.  Whenever a directive
  performs the same function as a UNIX TROFF directive, the name is the same.
  Unrecognized directives are ignored, and are not passed on to the output.
  Directives must be left justified and preceeded by a period.
  <P>
  Help text need not be formatted unless desired.  Filling and justification
  are NOT ENABLED unless a legal directive (other than "<TT>.nf</TT>") is given on the
  line immediately following the "<TT>.help</TT>" directive.
  <P>
  While filling, embedded whitespace in text IS significant to <B>lroff</B>,
  except at the end of a line.
  <B>lroff</B> recognizes no special characters.
  Blank lines cause a break, and are passed on to the output (a blank line
  is equivalent to "<TT>.sp</TT>"). 
  Case is not significant in command directives.
  Control characters embedded in text will be passed on to the output.
  <P>
  Since both whitespace and blank lines are significant, <B>lroff</B> will properly
  format ordinary paragraphs of text, and single line section headers,
  without need for embedded directives.
  <P>
  Since the i/o routines used by <B>lroff</B> are parameterized, pagination can be
  achieved by having the user supplied OUTPUT procedure count output lines.
  Similarly, pagination control directives can be added to the list of
  <B>lroff</B> directives, to be intercepted by the user supplied INPUT procedure.
  See the Manpage command for an example.
  <P>
  <P>
  DIRECTIVES
  <P>
  Most of the <B>lroff</B> directives function the same as in the UNIX text
  formatters.  For the benefit of readers without experience with UNIX,
  "<TT>filling</TT>" means collecting words of text until an output line has been
  filled, and "<TT>justification</TT>" refers to adding extra spaces between words
  to cause the output line to be both left and right justified (as in this
  paragraph).  Filling is disabled with NF, and resumes following a FI.
  While filling is disabled, only the control directives FI and RJ will be
  recognized.  Justification is enabled with JU, and disabled with NJ.
  The filling of an output line may be stopped, and the line output, with BR.
  SP (or a blank line) does the same thing, outputting one or more blank
  lines as well.  CE causes the current line to be broken, and outputs the
  next line of input, centered.
  <P>
  The directive "<TT>.rj text</TT>" breaks the current line, and outputs the next
  line of input, unfilled, with "<TT>text</TT>" right justified on the same line.
  RJ is especially useful for numbering equations.  The RJ directive is
  recognized whether or not filling is in effect.
  <P>
  SH and IH may be used for section headers.  Both cause a break, followed
  by a couple blank lines, followed by the next line of input,
  left justified on the output line.  The left margin is reset to its
  initial value.  If IH is used, the text following the section header will
  be indented one level in from the left margin.
  The number of lines of blank lines before the heading,
  and the amount of indentation, are optional arguments.
  The default values are shown in the request summary below.  If values
  other than the defaults are desired, they need only be supplied as arguments
  once.  Succeeding calls will continue to use the new values.
  <P>
  The IH and LS directives are especially useful in help text (manual pages).
  LS with a label string is useful for parameter lists,
  as shown in the example below.
  LS without a label string is used for relative indenting.
  A following LE restores the previous level of indentation.
  <P>
  The LS directive has the form "<TT>.ls [n] [stuff]</TT>", where "<TT>n</TT>" (optional)
  is the amount by which the following text is to be indented,
  and "<TT>stuff</TT>" is the (optional) label for the indented text block.
  LS causes a break, followed by one blank line, then the label string (if given),
  left justified.
  If the length of "<TT>stuff</TT>" is less than N-1 characters, the text
  block will start filling on the same line, otherwise on the next line.
  The indented text block may contain anything, including additional LS
  directives if nesting is desired.  A matching LE eventually terminates the
  block, restoring the previous level of indentation.
  <P>
  The LS directive takes the most recent argument as the new default
  indentation, allowing the argument to be omitted in subsequent calls.
  To keep the current default value from being changed, use a negative
  argument.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Example</H3>
  <! BeginSection: 'EXAMPLE'>
  <UL>
  <BR>
  Many examples of the use of the <B>lroff</B> command directives in help text
  can be found by browsing about in source listings.
  A brief example is included here for convenient reference.
  <BR>
  The "<TT>.help</TT>" directive, used to mark the beginning
  of a block of help text, is used by HELP and MANPAGE rather than <B>lroff</B>.
  The (optional) arguments to "<TT>.help</TT>" are the keyword name of the help
  text block, and two strings.
  The keyword argument may be a list of the form "<TT>.help keyw1,
  keyw2, ..., keywn</TT>", if more than one keyword is appropriate.
  The first keyword in the list is placed in the header of a manual page,
  followed by the first string, in parenthesis.  The second string,
  if given, is centered in the header line.  The strings need not be
  delimited unless they contain whitespace.
  <BR>
  The <B>lroff</B>-format help text fragment
  <BR>
  <DL>
  <DT><B></B></DT>
  <! Sec='EXAMPLE' Level=0 Label='' Line=' '>
  <DD><PRE>
  </DD>
  </DL>
  </UL>
  <! EndSection:   'EXAMPLE'>
  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  stcopy -- copy a string.
  </UL>
  <! EndSection:   'NAME'>
  <H3>Purpose</H3>
  <! BeginSection: 'PURPOSE'>
  <UL>
  Stcopy is used to copy an EOS delimited character
  string.  The EOS delimiter MUST be present.
  </UL>
  <! EndSection:   'PURPOSE'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  stcopy (from, to, maxchar)
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>from</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='from' Line='from'>
  <DD>The input string.
  </DD>
  </DL>
  <DL>
  <DT><B>to</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='to' Line='to'>
  <DD>The output string, of length no less than "maxchar"
  characters (excluding the EOS).
  </DD>
  </DL>
  <DL>
  <DT><B>maxchar</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='maxchar' Line='maxchar'>
  <DD>The maximum number of characters to be copied.
  Note that "maxchar" does not include the EOS.
  Thus, the destination string must contain storage
  for at least (maxchar + 1) characters.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  </PRE>
  <BR>
  <BR>
  </DD>
  </DL>
  would be converted by <B>lroff</B> (as called from Help) into something like
  the following.  Remember that the margins are runtime arguments to <B>lroff</B>.
  Help does not print a header line, or break pages.
  <BR>
  <BR>
  NAME
  stcopy -- copy a string.
  <BR>
  <BR>
  PURPOSE
  Stcopy  is  used  to  copy  an  EOS delimited character
  string.  The EOS delimiter MUST be present.
  <BR>
  <BR>
  USAGE
  stcopy (from, to, maxchar)
  <BR>
  <BR>
  PARAMETERS
  <DL>
  <DT><B>from</B></DT>
  <! Sec='DESCRIPTION' Level=-1 Label='from' Line='from'>
  <DD>The input string.
  </DD>
  </DL>
  <DL>
  <DT><B>to</B></DT>
  <! Sec='DESCRIPTION' Level=-1 Label='to' Line='to'>
  <DD>The output string, of length no less than "<TT>maxchar</TT>"
  characters (excluding the EOS).
  </DD>
  </DL>
  <DL>
  <DT><B>maxchar</B></DT>
  <! Sec='DESCRIPTION' Level=-1 Label='maxchar' Line='maxchar'>
  <DD>The maximum number of characters to be copied.
  Note that "<TT>maxchar</TT>" does not include the EOS.
  Thus, the destination string must contain storage
  for at least (maxchar + 1) characters.
  </DD>
  </DL>
  <BR>
  <BR>
  DESCRIPTION
  <BR>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  help
  <P>
  The reader should note that MANPAGE, which is page oriented,
  recognizes the following directives in addition to those recognized
  by <B>lroff</B>: BP (break page), and KS, KE (start and end keep).  MANPAGE also
  omits blank lines at the top of a page.  These directives may safely
  be included in <B>lroff</B> text, as they will be ignored by <B>lroff</B> if not
  intercepted by the procedure calling <B>lroff</B>.
  <P>
  </UL>
  <! EndSection:   'SEE ALSO'>
  <H3>Request summary</H3>
  <! BeginSection: 'REQUEST SUMMARY'>
  <UL>
  <BR>
  <PRE>
  Request Initial Default  Break		Meaning
  <P>
    .fi	  yes		  yes	Begin filling output lines.
    .nf	  no		  yes	Stop filling output lines.
    .ju	  yes		  no	Right justify output lines.
    .nj	  no		  no	Don't right justify.
    .rj text		  yes	Rt justify text on next line.
    .sh n		  n=2	  yes	Skip n lines, start section.
    .ih m n	m=2,n=5	  yes	Like SH, but indent n spaces.
    .br			  yes	Stop filling current line.
    .ce			  yes	Center following line.
    .sp n		  n=1	  yes	Space "n" lines.
    .in n	  n=0	  n=0	  yes	Set left margin to "current+n".
    .ls n	label	  n=8	  yes	Begin labeled text block.
    .le			  yes	End labeled text block.
  <P>
  additional directives provided by MANPAGE:
  <P>
    .bp			  yes	Start a new page of output.
    .tp n   n=4		  yes	Break page if &lt; n lines left.
    .ks			  yes	Begin saving output.
    .ke			  yes	Output saved text all on one page.
  </PRE>
  </UL>
  <! EndSection:    'REQUEST SUMMARY'>
  
  <! Contents: 'NAME' 'PURPOSE' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLE' 'NAME' 'PURPOSE' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'SEE ALSO' 'REQUEST SUMMARY'  >
  
