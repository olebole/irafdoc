netstatus — Print the status of the local network
=================================================

**Package: system**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>netstatus (Feb86)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>system</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>netstatus (Feb86)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>netstatus</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  netstatus -- print the status of the local network
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  netstatus
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  None.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <I>Netstatus</I> prints the status of the local network as perceived by the
  system process x_system.e (the network status may differ for each subprocess).
  The status output identifies the local node, lists all nodes in the local
  network, and lists all the aliases (recognized names) for each node.
  A message will be printed if networking is disabled on the local machine.
  The local network is defined by the table files "<TT>dev$hosts</TT>", "<TT>dev$uhosts</TT>",
  and "<TT>dev$hostlogin</TT>".
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  <P>
  <PRE>
  cl&gt; netstatus
  Local node `draco' (5), default node `draco', 12 nodes in local network
  <P>
      NODE SERVER NREFS STATUS  ALIASES
         1      0     0  00000  aquila vax1 a 1 class1 plot print
         2      0     0  00000  lyra vax2 b 2 class2
         3      0     0  00000  vela vax3 3 v class3
         4      0     0  00000  carina vax5 c 5 class5
         5      0     0  00000  draco vax6 6 d class6 0
         6      0     0  00000  tucana sun1 t
         7      0     0  00000  hydra sun2 h
         8      0     0  00000  mensa pc1 m
         9      0     0  00000  pictor pc2
        10      0     0  00000  octans sun3 o
        11      0     0  00000  pavo mvax1 p
        12      0     0  00000  volans lsi1
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>