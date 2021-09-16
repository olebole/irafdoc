.. _strings:

strings — String manipulation routines
======================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  strings -- string manipulation functions available in the CL
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  <PRE>
  str     (x)
  substr  (str, first, last)
  stridx  (test, str)
  strldx  (test, str)
  strlen  (str)
  strlwr  (str)
  strupr  (str)
  strstr  (str1, str2)
  strlstr (str1, str2)
  </PRE>
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The following functions are available for the manipulation of strings
  within the CL.  All string positions are returned as 1-indexed values.
  <P>
  <DL>
  <DT><B>str (x)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='str' Line='str (x)'>
  <DD>Converts its argument into a string.  The argument may be
  boolean, integer or real.
  </DD>
  </DL>
  <DL>
  <DT><B>substr (str, first, last)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='substr' Line='substr (str, first, last)'>
  <DD>Extracts a substring from string <I>str</I> from index <I>first</I> to 
  index <I>last</I>.  The <I>first</I> value may be larger than <I>last</I>, in 
  which case the returned string is reversed.  The first character in the 
  string is at index 1.
  </DD>
  </DL>
  <DL>
  <DT><B>stridx (test, str)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='stridx' Line='stridx (test, str)'>
  <DD>Finds the position of the first occurrence of any character found in <I>test</I>
  in the string <I>str</I>, returning 0 if the match fails.
  </DD>
  </DL>
  <DL>
  <DT><B>strldx (test, str)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='strldx' Line='strldx (test, str)'>
  <DD>Finds the position of the last occurrence of any character found in <I>test</I>
  in the string <I>str</I>, returning 0 if the match fails.
  </DD>
  </DL>
  <DL>
  <DT><B>strlen (str)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='strlen' Line='strlen (str)'>
  <DD>Returns the current length of a string.  Note that the maximum length may be
  obtained as the value of the expression `param.p_length'.
  </DD>
  </DL>
  <DL>
  <DT><B>strlwr (str)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='strlwr' Line='strlwr (str)'>
  <DD>Converts <I>str</I> to all lower-case characters, returns a string value.
  </DD>
  </DL>
  <DL>
  <DT><B>strupr (str)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='strupr' Line='strupr (str)'>
  <DD>Converts <I>str</I> to all upper-case characters, returns a string value.
  </DD>
  </DL>
  <DL>
  <DT><B>strstr (str1, str2)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='strstr' Line='strstr (str1, str2)'>
  <DD>Finds the position of the first occurrence of <I>str1</I> in <I>str2</I> (an
  exact match is required), or 0 if the match fails.
  </DD>
  </DL>
  <DL>
  <DT><B>strlstr (str1, str2)</B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='strlstr' Line='strlstr (str1, str2)'>
  <DD>Finds the position of the last occurrence of <I>str1</I> in <I>str2</I> (an
  exact match is required), or 0 if the match fails.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Simple function calls.
  <P>
  <PRE>
  	s = str(y)			     # convert y to a string.
  	s = substr  ("abcdefg", 2, 4)	     # s = "bcd"
  	s = substr  ("abcdefg", 4, 2)	     # s = "dcb"
  	i = stridx  ("abc", " eeboq")	     # i = 4
  	i = strldx  ("/", "/path/image.imh") # i = 6
  	i = strlen  ("abc")		     # i = 3
  	s = strlwr  ("ABC")		     # s = "abc"
  	s = strupr  ("abc")		     # s = "ABC"
  	i = strstr  ("imh","imhead.imh")     # i = 1
  	i = strlstr ("imh","imhead.imh")     # i = 8
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  scan, radix
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
