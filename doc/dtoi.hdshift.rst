hdshift — Align related HD curves
=================================

**Package: dtoi**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>hdshift (Feb87)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>imred.dtoi</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>hdshift (Feb87)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>hdshift</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  hdshift - calculate and subtract zero point to align HD curves.
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  hdshift database
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_database">database</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='database' Line='database'>
  <DD>Input list of databases containing density, exposure and fit information.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  For each file in <B>database</B>, procedure <B>hdshift</B> calculates and 
  subtracts a zero point shift to bring several related HD curves into
  alignment.  The individual shifts are calculated by elimination of the 
  first coefficient (Bevington, eqn 9-3):
  <PRE>
                  _      _      _               _
             a0 = y - a1*X - a2*X**2 - ... - an*X**n
  <P>
  </PRE>
  Here, the averages over y and X refer to individual <B>database</B> averages; 
  the coefficients a1, ... an were previously calculated using data from all 
  <B>database</B>s, in task <I>hdfit</I>, and stored in the database.  The
  a0 term is calculated individually for each database; this term represents
  the zero point shift in log exposure and will be different for each database.
  <P>
  On output, the log exposure values in each <B>database</B> have been 
  shifted to the zero point shift of the first database in the list.  The
  log exposure records are now aligned and it would be appropriate
  to run task <I>hdfit</I> on the modified <B>database</B> list and
  determine the common solution.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <PRE>
  <P>
  Shift the curves in four databases to a common zero point.  
  <P>
  	cl&gt; hdshift db1,db2,db3,db4
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  hdfit, hdtoi
  <BR>
  "<TT>Averaging Photographic Characteristic Curves</TT>", John Kormendy, from
  "<TT>ESO Workshop on Two Dimensional Photometry</TT>", Edited by P. Crane and
  K.Kjar, p 69, (1980), an ESO Publication.
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>