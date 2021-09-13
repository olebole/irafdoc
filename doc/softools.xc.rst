.. _xc:

xc — Compile and/or link a program
==================================

**Package: softools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  xc -- portable IRAF compile/link utility
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  xc [flags] files
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Flags</H3>
  <! BeginSection: 'FLAGS'>
  <UL>
  <DL>
  <DT><B>-a</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-a'>
  <DD>To support VMS link options file.  Next file is taken to be the VMS name
  of a link options file.  This is primarily for using long lists of files
  or libraries and not for actual VMS Linker options, since XC adds continuation
  characters where it believes it is appropriate.
  </DD>
  </DL>
  <DL>
  <DT><B>-C</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-C'>
  <DD>Tells fortran to do array bound and other checking.
  By default no checking is done.  From DCL fortran usually
  does array and overflow checking which is not used here.
  </DD>
  </DL>
  <DL>
  <DT><B>-c</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-c'>
  <DD>Tells <I>xc</I> not to link, i.e., not to create an executable.
  </DD>
  </DL>
  <DL>
  <DT><B>-d</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-d'>
  <DD>Causes debug messages to be printed during execution.
  </DD>
  </DL>
  <DL>
  <DT><B>-F, -f</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-F, -f'>
  <DD>Do not delete the Fortran translation of an SPP source file.
  </DD>
  </DL>
  <DL>
  <DT><B>-g</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-g'>
  <DD>Generates debugging information and (for VMS), links in the debugger.
  </DD>
  </DL>
  <DL>
  <DT><B>-h</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-h'>
  <DD>Causes the executable to be linked as a host program, i.e., without the
  IRAF main and without searching the IRAF libraries, unless explicitly
  referenced on the command line.  Used to compile and link host (e.g., Fortran)
  programs which may or may not reference the IRAF libraries.
  </DD>
  </DL>
  <DL>
  <DT><B>-i2</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-i2'>
  <DD>Tells fortran to use I*2 by default.
  </DD>
  </DL>
  <DL>
  <DT><B>-i4</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-i4'>
  <DD>Tells fortran to use I*4 by default.
  </DD>
  </DL>
  <DL>
  <DT><B>-l<I>lib</I></B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-l\fIlib\fR'>
  <DD>This tells the linker which libraries besides the standard
  ones to include.  These must be either on the current
  directory, or in an IRAF system library (lib$ or hlib$).
  The library specification must be immediately after the option as in
  "<TT>-lxtools</TT>".  No other option may follow the <TT>'l'</TT> option in the same
  argument as in -lxtoolsO.	
  </DD>
  </DL>
  <DL>
  <DT><B>-L</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-L'>
  <DD>Creates a list file. VMS specific.
  </DD>
  </DL>
  <DL>
  <DT><B>-M, -m</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-M, -m'>
  <DD>Tells the linker to create a link map.
  </DD>
  </DL>
  <DL>
  <DT><B>-n</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-n'>
  <DD>Not really supported under VMS since "<TT>normal</TT>" users
  cannot install images.  In Unix this is just a link
  option to make a shareable image.
  </DD>
  </DL>
  <DL>
  <DT><B>-N</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-N'>
  <DD>Same as -z for VMS.
  </DD>
  </DL>
  <DL>
  <DT><B>-Nh [filename]</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-Nh [filename]'>
  <DD>This tells xpp that the foreign definitions in the
  file specified should be used in preference to
  standard include files.	
  </DD>
  </DL>
  <DL>
  <DT><B>-o</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-o'>
  <DD>This flag redirects the output of the compile if used in
  conjunction with -c option or specifies where the executable
  or object is to be placed.  If not given the first file
  name is used to obtain the name for the executable or
  object.
  </DD>
  </DL>
  <DL>
  <DT><B>-O</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-O'>
  <DD>Optimize object code produced; this is now the default, but this switch
  is still provided for backwards compatibility.
  </DD>
  </DL>
  <DL>
  <DT><B>-p pkgname</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-p pkgname'>
  <DD>Load the package environment for the named external package, e.g.,
  "<TT>xc -c -p noao file.x</TT>".  If the same package is always specified
  the environment variable or logical name PKGENV may be defined at the
  host level to accomplish the same thing.  The package name <I>must</I>
  be specified when doing software development in an external or layered
  package.
  </DD>
  </DL>
  <DL>
  <DT><B>-P</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-P'>
  <DD>Check portability.  This should be used all of the time in IRAF,
  but the VMS C compiler forces the use of non-standard
  constructs in some cases.  Also &lt;stdio.h&gt; and &lt;ctype.h&gt; get
  complaints for the above reason.  This may be used and probably
  should when working with Fortran due to Dec non-standard
  extension.
  </DD>
  </DL>
  <DL>
  <DT><B>-q</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-q'>
  <DD>Disable optimization.  Opposite of -O.  Object code will be optimized
  by default.
  </DD>
  </DL>
  <DL>
  <DT><B>-s</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-s'>
  <DD>Strips all symbols and debugging information.
  </DD>
  </DL>
  <DL>
  <DT><B>-S</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-S'>
  <DD>Same as -s for VMS.
  </DD>
  </DL>
  <DL>
  <DT><B>-v</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-v'>
  <DD>Verbose mode.  Causes messages to be printed during execution telling
  what the <I>xc</I> program is doing.
  </DD>
  </DL>
  <DL>
  <DT><B>-w</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-w'>
  <DD>Suppress warnings.				
  </DD>
  </DL>
  <DL>
  <DT><B>-X, -x</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-X, -x'>
  <DD>Compile and link for debugging.  In VMS/IRAF, links in the VMS debugger
  and symbols.
  </DD>
  </DL>
  <DL>
  <DT><B>-z</B></DT>
  <! Sec='FLAGS' Level=0 Label='' Line='-z'>
  <DD>Create a non-shareable image (default).
  </DD>
  </DL>
  </UL>
  <! EndSection:   'FLAGS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  XC is a machine independent utility for compiling and linking IRAF
  tasks or files.  The XC utility may also be used to compile and/or link
  non-IRAF files and tasks.  The VMS version of XC supports all of the
  important flags except -D which VMS C doesn't support in any way.
  It can be used to generate fortran from xpp or ratfor code, to compile any
  number of files, and then link them if desired.  XC accepts and maps IRAF
  virtual filenames, but since it is a standalone bootstrap utility the
  environment is not passed, hence logical directories cannot be used.
  <P>
  The following extensions are supported by the VMS version of xc:
  It is suggested that everyone stick with the iraf virtual file name extensions.
  These are : .x, .r, .f, .c, .s, .o, .a, .e. The mapping of these to their
  VMS counterparts is:
  <P>
  <PRE>
  <PRE>
       .x -&gt; .x    SPP code
       .r -&gt; .r    Ratfor code
       .f -&gt; .for  Fortran code
       .c -&gt; .c    C code
       .s -&gt; .mar  Macro assembler code
       .o -&gt; .obj  Object module
       .a -&gt; .olb  Library file
       .e -&gt; .exe  Executable Image
  </PRE>
  </PRE>
  <P>
  <P>
  XC is available both in the CL, via the foreign task interface, and as
  a standalone DCL callable task.  Usage is equivalent in either case.  Upper
  case flags must be quoted to be recognized (the upper case flags will be
  done away with at some point).
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Any upper case flags in the following examples must be doubly quoted in
  the CL, singly quoted in VMS, to make it to XC without VMS mapping
  everything to one case.  Omit the "<TT>-x</TT>" flag on a UNIX system.
  <P>
  1. Compile and link the source file "<TT>mytask.x</TT>" to produce the executable
  "<TT>mytask.e</TT>".
  <P>
  	cl&gt; xc mytask.x
  <P>
  2. Translate the file "<TT>file.x</TT>" into Fortran.
  <P>
  	cl&gt; xc -f file.x
  <P>
  3. Compile but do not link "<TT>mytask.x</TT>" and the support file "<TT>util.x</TT>".
  <P>
  	cl&gt; xc -c file.x util.x
  <P>
  4. Now link these for debugging.
  <P>
  	cl&gt; xc -x file.o util.o
  <P>
  5. Link the same files without the VMS debug stuff, but link in the library
  -ldeboor (the DeBoor spline routines) as well.
  <P>
  	cl&gt; xc file.o util.o -ldeboor
  <P>
  XC is often combined with <I>mkpkg</I> to automatically maintain large packages
  or libraries.
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  The -S flag should generate assembler
  output but does not presently do so in the VMS version.  All case sensitive
  switches should be done away with in both the UNIX and VMS versions of the
  utility.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  mkpkg, generic
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'FLAGS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
