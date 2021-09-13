quadsections — Produce image section list for sections of quadformat images
===========================================================================

**Package: quadred**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>quadsections (Aug01)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.imred.quadred</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>quadsections (Aug01)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>quadsections</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  quadsections -- Create image sections
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  quadsplit images
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_images">images</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='images' Line='images'>
  <DD>List of image names for images in <B>quadformat</B>.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_window">window = "<TT>datasec</TT>" (datasec|trimsec|biassec)</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='window' Line='window = "datasec" (datasec|trimsec|biassec)'>
  <DD>Type of section to output.  The choices are "<TT>datasec</TT>" for the amplifier
  section which includes the bias if any is present, "<TT>trimsec</TT>" for the trim
  section, and "<TT>biassec</TT>" for the bias section.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_section">section = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='section' Line='section = ""'>
  <DD>Section to be overlapped.  The output sections will be the parts of the
  amplifier windows which are included within this section.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_template">template = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='template' Line='template = ""'>
  <DD>Template for producing the output.  The template replaces occurs of
  $I with the image name, $S with the section, and $A with the amplifier
  label.  If none is specified then the default template "<TT>$I$S\\n</TT>" is
  used which produces the image name with section separated by new-lines.
  The special characters "<TT>\n</TT>" is the new-line and the extra "<TT>\</TT>" is
  required to pass the new-line through to the formatting routine.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  Images in "<TT>quadformat</TT>" (see help topic <B>quadformat</B>) are broken down
  in sections and written to the standard output in a specified format.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. To print the default data sections.
  <P>
  <PRE>
      qu&gt; quadsec quad0072
      quad0072[1:1034,1:1024]
      quad0072[1163:2196,1:1024]
      quad0072[1:1034,1025:2048]
      quad0072[1163:2196,1025:2048]
  </PRE>
  <P>
  3. To apply an overlap section.
  <P>
  <PRE>
      qu&gt; quadsec quad0072 section=[1000:2000,1000:2000]
      quad0072[1000:1034,1000:1024]
      quad0072[1163:2000,1000:1024]
      quad0072[1000:1034,1025:2000]
      quad0072[1163:2000,1025:2000]
  </PRE>
  <P>
  2. To print the trim sections.
  <P>
  <PRE>
      qu&gt; quadsec quad0072 window=trimsec
      quad0072[11:1034,1:1024]
      quad0072[1163:2186,1:1024]
      quad0072[11:1034,1025:2048]
      quad0072[1163:2186,1025:2048]
  </PRE>
  <P>
  <P>
  4.  To make a custom output.
  <P>
  <PRE>
      qu&gt; quadsec quad0072 template="image=$I, section=$S, amplifier=$A\\n"
      image=quad0072, section=[1:1034,1:1024], amplifier=11
      image=quad0072, section=[1163:2196,1:1024], amplifier=12
      image=quad0072, section=[1:1034,1025:2048], amplifier=21
      image=quad0072, section=[1163:2196,1025:2048], amplifier=22
      qu&gt; quadsec quad0072 template="$I.$A,"
      quad0072.11,quad0072.12,quad0072.21,quad0072.22,
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  quadformat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>