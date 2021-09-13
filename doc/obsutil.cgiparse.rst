cgiparse — Parse STRING_QUERY environment variable into task parameters
=======================================================================

**Package: obsutil**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>cgiparse (Mar03)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>noao.obsutil</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>cgiparse (Mar03)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>cgiparse</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  cgiparse -- parse STRING_QUERY environment var. into parameters
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_synopsis">SYNOPSIS</A></H2>
  <! BeginSection: 'SYNOPSIS'>
  <UL>
  CGIPARSE parses the STRING_QUERY environment varabile and sets parameters.
  The string format is a list of task.param=value pairs which includes the
  standard QUERY string special characters <TT>'&'</TT>, <TT>'+'</TT>, and <TT>'%'</TT>.  This is
  intended to parse a query from a CGI script.
  </UL>
  <! EndSection:   'SYNOPSIS'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  cgiparse
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  There are no parameters.  The input is the value of the QUERY_STRING
  environment variable.
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  CGIPARSE parses the STRING_QUERY environment varabile and sets parameters.
  The string format is a list of task.param=value pairs which includes the
  standard QUERY string special characters <TT>'&'</TT>, <TT>'+'</TT>, and <TT>'%'</TT>.  This is
  intended to parse a query from a CGI script.
  <P>
  The only input is the STRING_QUERY variable.  If it is undefined the
  task simply does nothing.  The string will normally use the standard
  parameters for this type of string.  The data fields are task.param=value
  strings.  As each is parsed the values will be set for the task.  This
  assumes the tasks are defined.  Theere is no error checking for
  undefined tasks or parameters.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1.  A CGI script calls a CL script with the STRING_QUERY string set.
  The string has "<TT>imheader.longheader=yes</TT>".  CGIPARSE is called and
  when it completes the parameter value is set.
  <P>
  <PRE>
      cl&gt; lpar imhead
      cl&gt; lpar imheader
             images =                 image names
            (imlist = "*.imh,*.fits,*.pl,*.qp,*.hhh") default image ...
        (longheader = no)             print header in multi-line format
        (userfields = yes)            print the user fields ...
              (mode = "ql")           
      cl&gt; cgiparse
      cl&gt; lpar imheader
             images =                 image names
            (imlist = "*.imh,*.fits,*.pl,*.qp,*.hhh") default image ...
        (longheader = yes)            print header in multi-line format
        (userfields = yes)            print the user fields ...
              (mode = "ql")           
  </PRE>
  <P>
  Note that when running this in a "<TT>#!cl</TT>" script where the "<TT>login.cl</TT>" is
  not used that you must be careful to have all tasks referenced by the
  query string defined.
  <P>
  2.  Below is a "<TT>#!cl</TT>" type script that uses CGIPARSE.  It is used for
  a spectral exposure time calculator based on OBSUTIL.SPTIME though many
  aspects are fairly generic for this type of application.
  <P>
  <PRE>
  #!/iraf/iraf/bin.freebsd/cl.e -f
  <P>
  file	urldir
  <P>
  # The following must be set for different hosts.
  # The home directory and the urldir are the same but in different syntax.
  # The home directory must have a world writable tmp subdirectory.
  <P>
  set arch = ".freebsd"
  set (home = osfn ("/www/htdocs/noao/staff/brooke/gsmt/"))
  urldir = "/noao/staff/brooke/gsmt/"
  <P>
  # The uparm is a unique temporary directory.
  s1 = mktemp ("uparm") // "/"
  set (uparm = "home$/tmp/" // s1)
  mkdir uparm$
  cd uparm
  printf ("!/bin/chmod a+rw %s\n", osfn("uparm$")) | cl
  <P>
  # The URL directory is the same as uparm.
  urldir = urldir // "tmp/" // s1
  <P>
  # A private graphcap is required to give an path for sgidispatch.
  set graphcap = home$graphcap
  <P>
  # Load packages.
  dataio
  proto
  noao
  onedspec
  spectime
  gsmt
  <P>
  # Parse the CGI string and set parameters.
  cgiparse
  <P>
  # Create the output.
  <P>
  # Start HTML.
  printf ("Content-Type: text/html\n\n")
  printf ("&lt;html&gt;&lt;head&gt;&lt;title&gt;Test&lt;/title&gt;&lt;/head&gt;\n")
  printf ("&lt;body&gt;\n")
  if (cl.line == "...")
      printf ("&lt;center&gt;&lt;h2&gt;SPECTIME&lt;/h2&gt;&lt;/center&gt;\n", cl.line)
  else
      printf ("&lt;center&gt;&lt;h2&gt;%s&lt;/h2&gt;&lt;/center&gt;\n", cl.line)
  printf ("&lt;pre&gt;\n")
  <P>
  # Execute task(s).
  #show QUERY_STRING
  <P>
  setup interactive=no mode=h
  printf ("&lt;/pre&gt;\n")
  printf ("&lt;A Href='http://www.noao.edu/noao/staff/brooke/gsmt/gsmt.php?stage=1'&gt;Back to form&lt;/A&gt;")
  printf ("&lt;pre&gt;\n")
  <P>
  sptime output="counts,snr" graphics="g-gif" interactive=no mode=h
  <P>
  printf ("&lt;/pre&gt;\n")
  printf ("&lt;A Href='http://www.noao.edu/noao/staff/brooke/gsmt/gsmt.php?stage=1'&gt;Back to form&lt;/A&gt;\n")
  <P>
  printf ("&lt;pre&gt;\n")
  <P>
  # Add any gifs created.  We have to wait for them to be created.
  <P>
  gflush
  <P>
  i = 0; j = 1
  while (i != j) {
      sleep 2
      j = i
      files *.gif | count STDIN | scan (i)
  }
  <P>
  <P>
  if (i &gt; 0) {
      printf ("&lt;br&gt;&lt;p&gt;&lt;em&gt;Note: DN and S/N are per-pixel&lt;/em&gt;&lt;br&gt;\n")
  	
      files *.gif &gt; gifs
      list = "gifs"
      while (fscan (list, s1) != EOF) {
  	if (access (s1))
  		printf ("&lt;img src=\"%s%s\"&gt;\n", urldir, s1)
      }
      list = ""
      ## delete ("uparm$gifs", verify-)
  }
  <P>
  printf ("&lt;/pre&gt;\n")
  <P>
  # Finish HTML.
  <P>
  printf ("&lt;A Href='http://www.noao.edu/noao/staff/brooke/gsmt/gsmt.php?stage=1'&gt;Back to form&lt;/A&gt;")
  <P>
  printf ("&lt;/body&gt;&lt;/html&gt;\n")
  <P>
  # Clean up.
  ## delete ("*[^g][^i][^f]", verify-)
  <P>
  logout
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'SYNOPSIS' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
  </BODY>
  </HTML>