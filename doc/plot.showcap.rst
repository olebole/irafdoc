showcap — Show and decode graphcap entries
==========================================

**Package: plot**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>showcap (Jan86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>plot</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>showcap (Jan86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>showcap</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  showcap -- show and decode graphcap entries
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  showcap
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  None
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <B>Showcap</B> is an interactive, parameterless task that prints and interprets
  entries in the IRAF graphics device capability file dev$graphcap.  These
  entries contain device dimensions, character sizes etc. plus information for 
  encoding and decoding the ASCII control sequences sent to or returned by the
  device.  <B>Showcap</B> is thus mainly used by IRAF programmers for debugging
  new graphcap device entries.
  <P>
  At startup <B>showcap</B> prints the following instructions to STDOUT, then
  prompts with an asterisk.
  <PRE>
  <P>
  	cmd :  `set' device
  	    |  <TT>`*'</TT> (to dump full graphcap entry)
  	    |  cc [arg1 [arg2 [arg3]]]
  	    ;
  	
  	cc  :   a two character capcode (e.g., 'cm')
  	    |   an encoder program (non alpha first char)
  	    ;
  	*
  	
  </PRE>
  The user must first use `set' to tell <B>showcap</B> which graphics device to
  read from graphcap.  After a `set' or <TT>`*'</TT>, the full graphcap entry for the
  named device will be printed.  To view an individual capability, type the
  two-character capability name.
  <P>
  Some device capability entries take up to three arguments, which may be 
  listed on the same line after `cc', separated by whitespace.  <B>Showcap</B>
  is particularly useful for decoding the binary encoder entries used by the
  graphics kernels.  See the examples below.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Examine the graphcap entry for the Retrographics vt640.
  <P>
  <PRE>
  	cl&gt; showcap
  	  * set vt640		(dumps vt640 entry)
  </PRE>
  <P>
  2. Decode the sequence sent to the terminal for setting text height 2.
  <P>
  <PRE>
  	  * TH 2
  		    program:  ^[(1#47+.
  		    encoding: ^[1
  </PRE>
  <P>
  3. Decode the sequence sent to the terminal to set line type 3.
  <P>
  <PRE>
  	  * LT 3
  		    program:  LT=\E/(1$0)1d\E`($1-5)0d\E(1_+.$D)0d\E`($$:\<BR>
  		    encoding: ^[/0d^[b
  </PRE>
  <P>
  4. Set environment variable "<TT>graphcap</TT>" to your local test graphcap file, 
  set device to vt240 and examine the write-cursor (WC) command for
  x-coordinate 150, y-coordinate 350, and cursor 1.
  <P>
  <PRE>
  	cl&gt; set graphcap = "mytest.graphcap"
  	cl&gt; showcap
  	  * set vt240		(dumps vt240 entry)
  	  * WC 150 350 1
  		    program:  P[(1)%d,(2)%d]
  		    encoding: P[150,350]
  </PRE>
  <P>
  5. Examine the scan-cursor function returned when the user types key <TT>`a'</TT>
  from coordinate x=150, y=350 after a read-cursor request.
  <P>
  <PRE>
  	  * SC a[150,350]
  		    program:  (#0!1#0!2,!3,#0!8,#48-!99$0-91#10*9+!1#1!8
  			      $$8#1=#-39;#0!8,#48-!99$0-92#10*9+!2#1!8
  			      $$8#1=#-39;);
  		    X(R1)=150 Y(R2)=350, key = a
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  Diagnostics are mostly limited to a numeric status return when debugging
  binary encoder entries that contain bugs.
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  Graphics I/O Design Document.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>