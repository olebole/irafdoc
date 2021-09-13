.. _tokens:

tokens — Break a file up into a stream of tokens
================================================

**Package: lists**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  tokens -- break input into stream of tokens
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  tokens files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>files</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='files' Line='files'>
  <DD>The list of files to be converted into a stream of tokens.
  </DD>
  </DL>
  <DL>
  <DT><B>ignore_comments = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ignore_comments' Line='ignore_comments = yes'>
  <DD>Ignore comments in the input string?
  </DD>
  </DL>
  <DL>
  <DT><B>begin_comment = "<TT>#</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='begin_comment' Line='begin_comment = "#"'>
  <DD>The string marking the start of a comment
  </DD>
  </DL>
  <DL>
  <DT><B>end_comment = "<TT>eol</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='end_comment' Line='end_comment = "eol"'>
  <DD>The string marking the end of a comment.  The value <B>end_comment</B> = "<TT>eol</TT>"
  means the end of a line terminates a comment.
  </DD>
  </DL>
  <DL>
  <DT><B>newlines = yes</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='newlines' Line='newlines = yes'>
  <DD>Is newline a legal token?
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Task <I>tokens</I> breaks the input up into a series of tokens.
  The makeup of the
  various tokens is defined by the FMTIO primitive ctotok, which is not very 
  sophisticated, and does not claim to recognize the tokens for any particular
  language (though it does reasonably well for most modern languages).  Comments
  can be deleted if desired, and newlines may be passed on to the output as
  tokens.
  <P>
  Comments are delimited by user specified strings.  Only strings which are also
  recognized by ctotok() as legal tokens may be used as comment delimiters.
  If newline marks the end of a comment, the end_comment string should be given
  as "<TT>eol</TT>".  Examples of acceptable comment conventions are ("<TT>#</TT>", eol),
  ("/*"<TT>, "*/</TT>"), ("<TT>{</TT>", "<TT>}</TT>"), and ("<TT>!</TT>", eol).  Fortran style comments ("<TT>^{c}</TT>",eol)
  can be stripped by filtering with match beforehand.
  <P>
  Each token is passed to the output on a separate line.  Multiple newline
  tokens are compressed to a single token (a blank line).  If newline is not
  desired as an output token, it is considered whitespace and serves only to
  delimit tokens.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Break up the source file for this task into tokens:
  <P>
  	cl&gt; tokens tokens.x
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  words
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
