.. _package:

package — Define a new package, or print the current package names
==================================================================

**Package: language**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  package -- define a new package
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  package	pkgname
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>pkgname</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='pkgname' Line='pkgname'>
  <DD>The name of the new package to be created.  If called with no arguments,
  <I>package</I> lists the currently defined packages in task search order.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>package</I> task creates a new package.
  The newly defined package becomes the current package, and the prompt
  is changed to use the first two characters of the package name.
  The package command does not define any tasks within the package, that
  is done by subsequent <I>task</I> declarations.  Subsequent <I>task</I>
  declarations will add tasks to the task list for the new package.
  <P>
  The new package remains the "<TT>current package</TT>" until another <I>package</I>
  command is entered, or until the task in which the package command was
  entered is terminated.
  Normally <I>package</I> will be used at the beginning of a script to define
  the package name.  It will be followed by one or more task definitions,
  and then by a <I>cl</I> or <I>clbye</I> to interpret user commands,
  until the command <I>bye</I> is entered by the user, at which time the
  package script task terminates, discarding the package and any associated
  definitions.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. The use of <I>package</I> in a package script task.
  <P>
  <PRE>
  	package lists
  <P>
  	set	lists		= "pkg$lists/"
  <P>
  	task	table,
  		tokens,
  		unique,
  		lintran,
  		columns,
  		words		= "lists$x_lists.e"
  <P>
  	task	$gcursor	= "lists$gcursor.cl"
  	task	$imcursor	= "lists$imcursor.cl"
  	task	average		= "lists$average.cl"
  <P>
  	clbye()
  </PRE>
  <P>
  <P>
  2. List the currently defined packages in the order in which they will
  be searched for tasks.
  <P>
  <PRE>
  	cl&gt; pack
  	clpackage
  	language
  	user
  	system
  </PRE>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  All active packages must have unique names.  To eliminate the possibility
  of parameter file name collisions in UPARM, the three character string
  formed by concatenating the first two and final characters of the package
  name should be unique.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  task, redefine
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'BUGS' 'SEE ALSO'  >
  
