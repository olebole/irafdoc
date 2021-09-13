spy — Show processor status
===========================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>spy (Feb85)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>spy (Feb85)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>spy</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  spy -- tell who is logged in and what they are doing
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  spy [v]
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Spy</I> prints a summary of who is on the system and what they are doing.
  The optional argument <I>v</I> (short for <I>verbose</I>) causes more detailed
  information to be given.  The operation of this task is machine dependent,
  as is the quantity and format of the information returned.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  cl&gt; spy
    4:36pm  up 24 days,  5:42,  2 users,  load average: 0.29, 0.15, 0.18
  User     tty       login@  idle   JCPU   PCPU  what
  roger    ttyh8     4:21pm    15      8      5  -csh 
  alice    ttyh9     4:26pm           44     27  w 
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  diskspace
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>