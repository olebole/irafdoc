.. _mkpkg:

mkpkg — Make or update an object library or package
===================================================

**Package: softools**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  mkpkg - make or update a package or library
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  mkpkg [switches] [module ...] [name=value ...]
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Arguments</H3>
  <! BeginSection: 'ARGUMENTS'>
  <UL>
  <DL>
  <DT><B><B>-d[ddd]</B></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='\fB-d[ddd]\fR'>
  <DD>Debug mode.  Print detailed messages describing what <I>mkpkg</I> is doing.
  There are four levels of debug messages, selected by repeating the "<TT>d</TT>"
  character in the switch, e.g., "<TT>-d</TT>" is level one, "<TT>-dd</TT>" is level two, and
  so on.  The debug messages get progressively more detailed as the debug level
  increases.  Debug mode automatically enables the verbose mode messages.
  </DD>
  </DL>
  <DL>
  <DT><B><B>-f file</B></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='\fB-f file\fR'>
  <DD>Set the name of the file to be interpreted (default: "<TT>mkpkg</TT>").
  The special value "<TT>stdin</TT>" (lower case) allows commands to be entered
  interactively from the standard input, e.g., for debugging <I>mkpkg</I>.
  </DD>
  </DL>
  <DL>
  <DT><B><B>-i</B></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='\fB-i\fR'>
  <DD>Ignore errors.  Execution continues even if an error occurs.  In most cases
  it does anyhow, so this switch has little effect at present.
  </DD>
  </DL>
  <DL>
  <DT><B><B>-n</B></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='\fB-n\fR'>
  <DD>No execute.  Go through the motions, but do not touch any files.
  No execute mode automatically enables verbose mode (flag "<TT>-v</TT>").
  This switch should be used to verify new mkpkg files before execution.
  </DD>
  </DL>
  <DL>
  <DT><B><B>-p </B><I>pkgname</I></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='\fB-p \fIpkgname\fR'>
  <DD>Load the package environment for the named external package, e.g.,
  "<TT>mkpkg -p noao update</TT>".  If the same package is always specified
  the environment variable or logical name PKGENV may be defined at the
  host level to accomplish the same thing.  The package name <I>must</I>
  be specified when doing software development in an external or layered
  package.
  </DD>
  </DL>
  <DL>
  <DT><B><B>-u</B>    [AOSVS/IRAF only]</B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='\fB-u\fR    [AOSVS/IRAF only]'>
  <DD>Forcibly update the dates of improperly dated library modules.  This option
  is used when a binary archive is restored on a machine which cannot restore
  the file modify dates.  In this case, all source file dates would appear to
  have been modified since the libraries were updated, causing all sources to
  be recompiled.  By running <I>mkpkg</I> with the <I>-u</I> flag, one can update
  the library module dates without recompiling the associated files.  This is
  done by setting the date of each library module to be no older than the
  file <I>hlib$iraf.h</I>, which should be "<TT>touched</TT>" after the system has fully
  been restored to disk to mark the installation time.  Note that files which
  have been modified <I>since</I> the system was restored to disk will still
  cause the affected library modules to be updated, even when the <I>-u</I> flag
  is specfied.
  </DD>
  </DL>
  <DL>
  <DT><B><B>-v</B></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='\fB-v\fR'>
  <DD>Verbose mode.  A message is printed whenever a file is touched.
  Recommended when running large mkpkg jobs in batch mode.
  </DD>
  </DL>
  <DL>
  <DT><B><B>module</B></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='\fBmodule\fR'>
  <DD>The names of the module or modules (named entries in the "<TT>mkpkg</TT>" file) to be
  executed.  If no module is named the first module encountered is executed,
  unless a <I>mkpkg</I> macro preprocessor directive at the beginning of the file
  specifies a different default action.
  </DD>
  </DL>
  <DL>
  <DT><B><B>name=value [name=value...]</B></B></DT>
  <! Sec='ARGUMENTS' Level=0 Label='' Line='\fBname=value [name=value...]\fR'>
  <DD>Enter the named symbol/value pair into the symbol table of the <I>mkpkg</I>
  macro preprocessor.  The symbols <I>XFLAGS</I> (for the XC compiler) and
  <I>LFLAGS</I> (for the linker) are predefined but may be redefined on the
  command line.  Case is ignored in symbol names for portability reasons.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'ARGUMENTS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>mkpkg</I> utility is used to make or update IRAF packages or libraries.
  <I>Mkpkg</I> is used to bootstrap the IRAF system hence is implemented as
  a foreign task, callable either from within the IRAF environment or from the
  host system.  Usage is identical in either case (except that the details of
  when a particular argument may need to be quoted will vary depending on the
  command language used).  <I>Mkpkg</I> is upwards compatible with the old
  <I>mklib</I> utility.
  <P>
  <P>
  1. <B>Introduction</B>
  <P>
      <I>Mkpkg</I> provides two major facilities: a library update capability and
  a macro preprocessor.  The macro preprocessor provides symbol definition and
  replacement, conditional execution, and a number of builtin commands.
  The usefulness of these facilities is enhanced by the ability of <I>mkpkg</I>
  to update entire directory trees, or to enter the hierarchy of <I>mkpkg</I>
  descriptors at any level.  For example, typing "<TT>mkpkg</TT>" in the root directory
  of IRAF will make or update the entire system, whereas in the "<TT>iraf$sys</TT>"
  directory <I>mkpkg</I> will update only the system libraries, and in the
  "<TT>iraf$sys/fio</TT>" directory <I>mkpkg</I> will update only the FIO portion of the
  system library "<TT>libsys.a</TT>".
  <P>
  The <I>mkpkg</I> utility is quite simple to use to maintain small packages
  or libraries, despite the complexity of the discussion which follows.
  The reader is encouraged to study several examples of working mkpkg-files
  before reading further; examples will be found throughout the IRAF system.
  The mkpkg files for applications packages tend to be very similar to one
  another, and it is quite possible to successfully copy and modify the
  mkpkg-file from another package without studying the reference information
  given here.
  <P>
  <P>
  2. <B>Lexical Conventions</B>
  <P>
      The lexical conventions employed in <I>mkpkg</I> are those used throughout
  IRAF.  Comments may occur anywhere, begin with the character #, and extend
  to the end of the current line.  Blank lines are ignored virtually everywhere.
  Newline may be escaped with backslash to continue on the next line.
  All filenames are IRAF virtual filenames with the following extensions.
  <P>
  <P>
  <PRE>
  <PRE>
  	.a		object library
  	.c		C source
  	.e		executable (e.g., "x_package.e")
  	.f		Fortran source
  	.gc		generic C source
  	.gx		generic SPP source
  	.h		C or SPP header file
  	.inc		include file
  	.l		Lex source
  	.o		object file
  	.r		Ratfor source
  	.s		assembler source
  	.y		Yacc source
  </PRE>
  </PRE>
  <P>
  <P>
  Since <I>mkpkg</I> is an IRAF utility it recognizes the major IRAF logical
  directories; these are summarized in the list below.  The IRAF (or UNIX)
  pathname convention is used to specify pathnames rooted in the current
  directory or a logical directory.
  <P>
  <P>
  <PRE>
  <PRE>
  	as$		where .s files go		host$as/
  	bin$		installed executables		iraf$bin/
  	dev$		device tables			iraf$dev/
  	hlib$		machdep header files		host$hlib/
  	host$		host system interface		[MACHDEP]
  	iraf$		the root directory of IRAF	[MACHDEP]
  	lib$		system library			iraf$lib/
  	math$		math sources			iraf$math/
  	pkg$		applications packages		iraf$pkg/
  	sys$		the VOS, system libraries	iraf$sys/
  	tmp$		where temporary files go	[MACHDEP]
  </PRE>
  </PRE>
  <P>
  <P>
  All other directories should be referenced by giving the path from either the
  current directory or from one of the system logical directories shown above.
  For example, "<TT>pkg$system/</TT>" is the root directory of the SYSTEM package,
  and "<TT>..</TT>" is the directory one level up from the current directory.
  <P>
  <P>
  3. <B>Maintaining Libraries with MKPKG</B>
  <P>
      Libraries are described by a <B>member list</B> module in the "<TT>mkpkg</TT>" file.
  The syntax of a library member list module is shown below.  Note that the
  <B>mkpkg</B> module name for a library member list module is the same as the
  name of the actual library, hence must end with the extension "<TT>.a</TT>".
  <P>
  <P>
  <PRE>
  <PRE>
  	libname.a:
  		member1		dep1 dep2 ... depN
  		member2		dep1 dep2 ... depN
  		  ...
  		memberN		dep1 dep2 ... depN
  		;
  </PRE>
  </PRE>
  <P>
  <P>
  Here, "<TT>libname.a</TT>" is the IRAF virtual filename of the library (regardless of
  what directory it resides in), "<TT>memberN</TT>" is the name of a source file which
  may contain any number of actual library object modules, and "<TT>depN</TT>" is the
  name of a file upon which the named member depends.  If any of the named
  dependency files is newer than the corresponding member source file, or if
  the member source file is newer than the compiled library object module,
  the source file is recompiled and replaced in the library.  Both source
  files and dependency files may reside in remote directories.  The names of
  dependency files in system libraries should be enclosed in &lt;&gt; delimiters,
  e.g., "<TT>&lt;fset.h&gt;</TT>".  Each member must be described on a separate line.
  <P>
  If the library being updated does not reside in the current directory
  (directory from which the "<TT>mkpkg</TT>" command was entered) then the library must
  be "<TT>checked out</TT>" of the remote directory before it can be updated, and checked
  back in when updating is complete.  These operations are performed by macro
  preprocessor directives, e.g.:
  <P>
  <P>
  <PRE>
  <PRE>
  	$checkout libsys.a lib$
  	$update   libsys.a
  	$checkin  libsys.a lib$
  	$exit
  <P>
  	libsys.a:
  		@symtab		# update libsys.a in ./symtab
  		brktime.x	&lt;time.h&gt;
  		environ.x	environ.com environ.h &lt;ctype.h&gt;\<BR>
  				&lt;fset.h&gt; &lt;knet.h&gt;
  		main.x		&lt;clset.h&gt; &lt;config.h&gt; &lt;ctype.h&gt;\<BR>
  				&lt;error.h&gt; &lt;fset.h&gt; &lt;knet.h&gt;\<BR>
  				&lt;printf.h&gt; &lt;xwhen.h&gt;
  		onentry.x	&lt;clset.h&gt; &lt;fset.h&gt; &lt;knet.h&gt;
  		spline.x	&lt;math.h&gt; &lt;math/interp.h&gt;
  		;
  </PRE>
  </PRE>
  <P>
  <P>
  Note that the checkout operation is required only in the directory from which
  the "<TT>mkpkg</TT>" command was entered, since the library has already been checked
  out when the mkpkg-file in a subdirectory is called to update its portion
  of the library (as in the "<TT>@symtab</TT>" in the example above).  The checkout
  commands should however be included in each mkpkg-file in a hierarchy in such
  a way that the library will be automatically checked out and back in if
  <I>mkpkg</I> is run from that directory.  The checkout commands are ignored
  if the mkpkg-file is entered when updating the library from a higher level,
  because in that case <I>mkpkg</I> will search for the named entry for the
  library being updated, ignoring the remainder of the mkpkg-file.
  <P>
  Sometimes it is necessary or desirable to break the library member list up
  into separate modules within the same mkpkg-file, e.g., to temporarily
  change the value of the symbol XFLAGS when compiling certain modules.
  To do this use the "<TT>@</TT>" indirection operator in the primary module list to
  reference a named sublist, as in the example below.  Normal indirection
  cannot be used unless the sublist resides in a subdirectory or in a different
  file in the current directory, e.g., "<TT>@./mki2</TT>", since a single mkpkg-file
  cannot contain two modules with the same name.  The same restrictions apply
  to the <I>$update</I> operator.
  <P>
  <P>
  <PRE>
  <PRE>
  	libpkg.a:
  		@(i2)
  		alpha.x
  		beta.x
  		zeta.f
  		;
  	i2:
  		$set	XFLAGS = "-cO -i2"
  		gamma.f
  		delta.f
  		;
  </PRE>
  </PRE>
  <P>
  <P>
  In the example above five object modules are to be updated in the library
  "<TT>libpkg.a</TT>".  The files listed in module "<TT>i2</TT>", if out of date, will be compiled
  with the nonstandard XFLAGS (compiler flags) specified by the <I>$set</I>
  statement shown.
  <P>
  <P>
  4. <B>The MKPKG Macro Preprocessor</B>
  <P>
      The <I>mkpkg</I> macro preprocessor provides a simple recursive symbol
  definition and replacement facility, an include file facility, conditional
  execution facilities, an OS escape facility, and a number of builtin directives.
  The names of the preprocessor directives always begin with a dollar sign;
  whitespace is not permitted between the dollar sign and the remainder of the
  name.  Several preprocessor directives may be given on one line if desired.
  Preprocessor directives are executed as they are encountered, and may appear
  anywhere, even in the member list for a library.
  <P>
  <P>
  4.1 Symbol Replacement
  <P>
      Symbol substitution in the <I>mkpkg</I> macro preprocessor is carried out
  at the character level rather than at the token level, allowing macro expansion
  within tokens, quoted strings, or OS escape commands.  Macros are recursively
  expanded but may not have arguments.
  <P>
  Macros may be defined on the <B>mkpkg</B> command line, in the argument list
  to a <B>$call</B> or <B>$update</B> directive (see below), in an include file
  referenced with the <B>$include</B> directive, or in a <B>$set</B> directive.
  All symbols are global and hence available to all lower level modules,
  but symbols are automatically discarded whenever a module exits, hence cannot
  affect higher level modules.  A local symbol may redefine a previously
  defined symbol.  The IRAF and host system environment is treated as an
  extension of the <B>mkpkg</B> symbol table, i.e., a logical directory such
  as "<TT>iraf</TT>" may be referenced like a locally defined symbol.
  <P>
  Macro replacement occurs only when explicitly indicated in the input text,
  as in the following example, which prints the pathname of the
  <B>dev$graphcap</B> file on the <B>mkpkg</B> standard output.  The sequence
  "<TT>$(</TT>" triggers macro substitution.  The value of a symbol may be obtained
  interactively from the standard input by adding a question mark after the
  left parenthesis, i.e., "<TT>$(?terminal)</TT>" (this does not work with the -f stdin
  flag).  The contents of a file may be included using the notation
  "<TT>$(@<I>file</I>)"<TT>.   Note that case is ignored in macro names; by convention,
  logical directories are normally given in lower case, and locally defined
  symbols in upper case.
  <P>
  <P>
  <PRE>
  <PRE>
  	$echo $(dev)graphcap
  	!xc $(XFLAGS) filea.x fileb.x
  </PRE>
  </PRE>
  <P>
  <P>
  Symbols are most commonly defined locally with the <B>$set</B> directive.
  The <B>$include</B> directive is useful for sharing symbols amongst different
  modules, or for isolating any machine dependent definitions in a separate
  file.  The IRAF <B>mkpkg</B> system include file <B>hlib$mkpkg.inc</B> is
  automatically included whenever <I>mkpkg</I> is run.
  <DL>
  <DT><B></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=''>
  <DD><DL>
  <DT><B><B>$set</B> symbol = value</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$set\fR symbol = value'>
  <DD>Enter the named symbol into the symbol table with the given string value.
  Any existing symbol will be silently redefined.  Symbols defined within a
  module are discarded when the module exits.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$include</B> filename</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$include\fR filename'>
  <DD>Read commands (e.g., <B>$set</B> directives) from the named include file.
  The include filename may be any legal virtual filename, but only the
  major logical directories are recognized, e.g., "<TT>iraf$</TT>", "<TT>host$</TT>", "<TT>hlib$</TT>",
  "<TT>lib$</TT>", "<TT>pkg$</TT>", and so on.
  </DD>
  </DL>
  </DD>
  </DL>
  <P>
  <P>
  The use of the <B>$set</B> directive is illustrated in the example below.
  Note the doubling of the preprocessor meta-character to avoid macro expansion
  when entering the value of the GEN macro into the symbol table.  The sequence
  "<TT>$$</TT>" is replaced by a single "<TT>$</TT>" whenever it is encountered in the input
  stream.
  <P>
  <P>
  <PRE>
  <PRE>
  	$set GFLAGS = "-k -t silrdx -p ak/"
  	$set GEN    = "$generic $$(GFLAGS)"
  <P>
  	ifolder (amulr.x, amul.x) $(GEN) amul.x $endif
  </PRE>
  </PRE>
  <P>
  <P>
  4.2 Conditional Execution
  <P>
      Conditional control flow is implemented by the <B>$if</B> directives
  introduced in the last example and described below.  The character "<TT>n</TT>" may
  be inserted after the "<TT>$if</TT>" prefix of any directive to negate the sense of
  the test, e.g., "<TT>$ifndef</TT>" tests whether the named symbol does not exist.
  Nesting is permitted.
  <DL>
  <DT><B></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=''>
  <DD><DL>
  <DT><B><B>$ifdef</B> (symbol [, symbol, ...])</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$ifdef\fR (symbol [, symbol, ...])'>
  <DD><BR>
  Test for the existence of one of the named symbols.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$ifeq</B> (symbol, value [, value,...])</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$ifeq\fR (symbol, value [, value,...])'>
  <DD><BR>
  Test if the value of the named symbol matches one of the listed value strings.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$iferr</B></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$iferr\fR'>
  <DD><BR>
  Test for an error return from the last directive executed which touched
  a file.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$iffile</B> (file [, file,...])</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$iffile\fR (file [, file,...])'>
  <DD><BR>
  Test for the existence of any of the named files.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$ifnewer</B> (file, filea)</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$ifnewer\fR (file, filea)'>
  <DD><B>$ifnewer</B> (file: filea [, fileb, ...])
  <BR>
  Test if the named file is newer (has been modified more recently) than
  any of the named files to the right.  The colon syntax may be used for
  clarity when comparing one file to many, but a comma will do.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$ifolder</B> (file, filea)</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$ifolder\fR (file, filea)'>
  <DD><B>$ifolder</B> (file: filea [, fileb, ...])
  <BR>
  Test if the named file is older than any of the named files.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$else</B></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$else\fR'>
  <DD><BR>
  Marks the <I>else</I> clause of an <I>if</I> statement.  The <I>else-if</I>
  construct is implemented as "<TT>$else $if</TT>", i.e., as a combination of the two
  more primitive constructs.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$endif</B></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$endif\fR'>
  <DD><BR>
  Terminates a $if or $if-$else statement.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$end</B></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$end\fR'>
  <DD><BR>
  Terminates an arbitrary number of $if or $if-$else statements.  This is most
  useful for terminating a long list of $if-$else clauses, where the alternative
  would be a long string of $endif directives.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$exit</B></B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$exit\fR'>
  <DD>Terminate the current program; equivalent to a semicolon, but the latter
  is normally used only at the end of the program to match the colon at the
  beginning, whereas <B>$exit</B> is used in conditionals.
  </DD>
  </DL>
  </DD>
  </DL>
  <P>
  <P>
  4.3 Calling Modules
  <P>
      The following preprocessor directives are available for calling <I>mkpkg</I>
  modules or altering the normal flow of control.
  <DL>
  <DT><B></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=' '>
  <DD><DL>
  <DT><B><B>$call</B> module[@subdir[/file]] [name=value] [name=value...]</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$call\fR module[@subdir[/file]] [name=value] [name=value...]'>
  <DD><BR>
  Call the named mkpkg-file module as a subroutine.  In most cases the called
  module will be in the current mkpkg-file, but the full module name syntax
  permits the module to be in any file of any subdirectory ("./file"<TT> references
  a different file in the current directory).  Arguments may be passed to
  the called module using the symbol definition facility; any symbols
  defined in this fashion are available to any modules called in turn by
  the called module, but the symbols are discarded when the called module returns.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$update</B> module[@subdir[/file]] [name=value] [name=value...]</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$update\fR module[@subdir[/file]] [name=value] [name=value...]'>
  <DD><BR>
  Identical to <B>$call</B> except that the named module is understood to
  be a library member list.  The current value of the symbol XFLAGS is used
  if XC is called to compile any files.  If the named library does not exist
  one will be created (a warning message is issued).
  </DD>
  </DL>
  <DL>
  <DT><B><B>$goto</B> label</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$goto\fR label'>
  <DD><BR>
  Causes execution to resume at the line following the indicated label.
  The syntax of a goto label is identical to that of a mkpkg-file module name,
  i.e., a line starting with the given name followed by a colon.
  The <I>$goto</I> statement automatically cancels any <I>$if</I> nesting.
  </DD>
  </DL>
  </DD>
  </DL>
  <P>
  <P>
  4.4 Preprocessor Directives
  <P>
      The remaining preprocessor directives are described below in alphabetical
  order.  Additional capability is available via OS escapes, provided the
  resultant machine dependence is acceptable.
  <DL>
  <DT><B></B></DT>
  <! Sec='DESCRIPTION' Level=0 Label='' Line=' '>
  <DD><DL>
  <DT><B><B>$echo</B> message</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$echo\fR message'>
  <DD><BR>
  Print the given message string on the standard output.  The string must be
  quoted if it contains any spaces.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$checkout</B> file directory</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$checkout\fR file directory'>
  <DD><BR>
  Check the named file out of the indicated directory.  The checkout operation
  makes the file accessible as if it were in the current directory; checkout
  is implemented either as a symbolic link or as a physical file copy depending
  upon the host system.  The referenced directory may be a logical directory,
  e.g., "<TT>lib$</TT>", or a path, e.g, "<TT>pkg$images/</TT>".  Checkout is not disabled by
  the "<TT>-n</TT>" flag.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$checkin</B> file directory</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$checkin\fR file directory'>
  <DD><BR>
  Check the named file back into the indicated directory.  The checkin operation
  is implemented either as a remove link or copy and delete depending upon the
  host system.  Checkin is not disabled by the "<TT>-n</TT>" flag.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$copy</B> filea fileb</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$copy\fR filea fileb'>
  <DD><BR>
  Make a copy <I>fileb</I> of the existing file <I>filea</I>.  On a UNIX host
  the copy operation will preserve the file modify date if the file is a library
  (to avoid the "<TT>symbol table out of date</TT>" syndrome).
  </DD>
  </DL>
  <DL>
  <DT><B><B>$delete</B> file [file ...]</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$delete\fR file [file ...]'>
  <DD><BR>
  Delete the named file or files.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$generic</B> [-k] [-p prefix] [-t types] [-o root] files</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$generic\fR [-k] [-p prefix] [-t types] [-o root] files'>
  <DD><BR>
  Run the generic preprocessor on the named files.  The generic preprocessor
  is an IRAF bootstrap utility and may not be available on non-UNIX hosts.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$link</B> [switches] file1 file2 ... fileN [-o file.e]</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$link\fR [switches] file1 file2 ... fileN [-o file.e]'>
  <DD><BR>
  Call XC with the given argument list to link the indicated files and libraries.
  The value of the symbol LFLAGS (default value the null string) is automatically
  inserted at the beginning of the command line.  This is equivalent to
  "<TT>!xc $(LFLAGS) ...</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><B>$move</B> file destination</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$move\fR file destination'>
  <DD><BR>
  Move the named file to the indicated directory, or rename the file in the
  current directory.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$omake</B> file [dep1] [dep2 ...]</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$omake\fR file [dep1] [dep2 ...]'>
  <DD><BR>
  Compile the named source file if it does not have a corresponding object file
  in the current directory, if the object file is older, or if any of the
  listed dependency files are newer (or not found).  The current value of the
  symbol XFLAGS is used if XC is called to compile the file.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$purge</B> directory</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$purge\fR directory'>
  <DD><BR>
  Delete all old versions of all files in the named directory.  Nothing is done
  if the system does not support multiple file versions.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$special</B> directory : filelist ;</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$special\fR directory : filelist ;'>
  <DD><BR>
  Add one or more files to the special file list for the host system.  This is
  a system facility, not intended for use in applications <I>mkpkg</I> files.
  The special file list is a list of all source files needing special processing
  for the local host system.  Examples of special files are files which are
  optimized in assembler (or some other nonstandard language), or files which
  must be compiled in a special way to get around bugs in a host compiler.
  The special file list makes it possible to flag arbitrary files for special
  processing, without having to modify the standard software distribution.
  In the IRAF system, the special file list is defined in the file
  "<TT>hlib$mkpkg.sf</TT>" which is included automatically by "<TT>hlib$mkpkg.inc</TT>" whenever
  <I>mkpkg</I> is run.
  <P>
  The syntax of a <I>filelist</I> entry is as follows:
  <P>
  	modname source_file mkobj_command
  <P>
  where <I>modname</I> is the filename of a library module as it appears in a
  library module list for the named directory, <I>source_file</I> is the virtual
  pathname of the source file to be used in lieu of the standard portable
  source file <I>modname</I>, and <I>mkobj_command</I> is the <I>mkpkg</I> command
  (e.g., $xc or an OS escape) to be executed to compile the named module.
  The character "<TT>&amp;</TT>" appearing in either the source file name or mkobj command
  is replaced by <I>modname</I>.  If the <I>mkobj_command</I> is omitted the
  specified source file will be compiled with $XC using the current value of
  XFLAGS.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$xc</B> [switches] file1 file2 ... fileN</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$xc\fR [switches] file1 file2 ... fileN'>
  <DD><BR>
  Call the XC compiler to compile the named files.  Note that the value of
  the symbol XFLAGS is <I>not</I> used when XC is explicitly called in this
  fashion (XFLAGS is used by <B>$update</B> and <B>$omake</B>).
  </DD>
  </DL>
  <DL>
  <DT><B><B>$debug</B> [on|off]</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$debug\fR [on|off]'>
  <DD><BR>
  Turn debug mode on or off.  If no argument is supplied debug mode is turned
  on.  Turning on debug mode automatically enables verbose mode.
  </DD>
  </DL>
  <DL>
  <DT><B><B>$verbose</B> [on|off]</B></DT>
  <! Sec='DESCRIPTION' Level=1 Label='' Line='\fB$verbose\fR [on|off]'>
  <DD><BR>
  Turn verbose mode on or off.  If no argument is supplied verbose mode is turned
  on.
  </DD>
  </DL>
  </DD>
  </DL>
  <P>
  <P>
  5. Error Recovery
  <P>
      <B>Mkpkg</B> is implemented in such a way that it is restartable.  If a mkpkg
  operation terminates prematurely for some reason, e.g., because of a compile
  error, execution error (such as cannot find the mkpkgfile in a subdirectory),
  interrupt, etc., then the mkpkg command can be repeated after correcting
  the error, without repeating the operations already completed.  If <B>mkpkg</B>
  is interrupted it may leave checked out files, objects compiled but not yet
  updated in a library, etc. lying about, but this is harmless and the
  intermediate files will be cleaned up when the errors have been corrected
  and the run successfully completes.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  Update the current package.
  <P>
  	cl&gt; mkpkg
  <P>
  Update the package library but do not relink.
  <P>
  	cl&gt; mkpkg libpkg.a
  <P>
  Make a listing of the package.
  <P>
  	cl&gt; mkpkg listing
  <P>
  <P>
  <PRE>
  <PRE>
  Sample mkpkg-file for the above commands:
  <P>
  <P>
  	# Make my package.
  <P>
  	$call relink
  	$exit
  <P>
  	relink:
  		$update	libpkg.a
  		$omake	x_mypkg.x
  		$link   x_mypkg.o -lxtools
  		;
  <P>
  	libpkg.a:
  		task1.x		pkg.h
  		task2.x
  		filea.x		pkg.com pkg.h &lt;fset.h&gt;
  		fileb.x		pkg.com
  		;
  <P>
  	listing:
  		!pr task1.x task2.x file[ab].x | vpr -Pvup
  		;
  </PRE>
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  xc, generic, softools package
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'ARGUMENTS' 'DESCRIPTION' 'EXAMPLES' 'SEE ALSO'  >
  
