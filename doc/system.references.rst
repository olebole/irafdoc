.. _references:

references — Find all help database references for a given topic
================================================================

**Package: system**

.. raw:: html

  <H3>Name</H3>
  <! BeginSection: 'NAME'>
  <UL>
  references -- find all help database references to a given topic
  </UL>
  <! EndSection:   'NAME'>
  <H3>Usage</H3>
  <! BeginSection: 'USAGE'>
  <UL>
  references topic
  </UL>
  <! EndSection:   'USAGE'>
  <H3>Parameters</H3>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B>topic</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='topic' Line='topic'>
  <DD>The topic for which help is desired, i.e., a keyword, phrase, or pattern
  which the help database or quick-reference file is to be searched for.
  </DD>
  </DL>
  <DL>
  <DT><B>quickref = "<TT>uparm$quick.ref</TT>"</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='quickref' Line='quickref = "uparm$quick.ref"'>
  <DD>The name of the optional quick-reference file.
  </DD>
  </DL>
  <DL>
  <DT><B>updquick = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='updquick' Line='updquick = no'>
  <DD>Create or update the quick-reference file, e.g., because new packages
  have been added to the global help database.  Updating the quick-reference
  file automatically enables <I>usequick</I>, discussed below.
  </DD>
  </DL>
  <DL>
  <DT><B>usequick = no</B></DT>
  <! Sec='PARAMETERS' Level=0 Label='usequick' Line='usequick = no'>
  <DD>Use the quick-reference file.  By default, a runtime search of all the package
  menus in the full help database is performed, which ensures that all packages
  are searched, but which is comparatively slow.
  </DD>
  </DL>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H3>Description</H3>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  The <I>references</I> task is used to search the help database for all tasks
  or other help modules pertaining to the given topic, where <I>topic</I> may be
  a keyword, phrase, or any general pattern as would be input to the <I>match</I>
  task.  By default the full help database will be searched.  If desired,
  the "<TT>one-liner</TT>" information used for topic searching may be extracted and
  used to prepare a quick-reference file to speed further searches.
  This is not done by default because the help database is too dynamic, e.g., 
  new external packages may be installed at any time, by any user, or new
  tasks may be added to existing packages at any time.
  <P>
  References to tasks (or other objects) are printed in the form
  <P>
  <PRE>
         keyword1 - one line description
         keyword2 - one line description
  </PRE>
  <P>
  and so on.  To determine the <I>package pathname</I> of each named task,
  get <I>help</I> on the named <I>keyword</I> and the pathname will be seen at
  the top of the help screen, followed by additional information about the
  referenced object.  If there are multiple objects with the same name,
  a "<TT>help &lt;keyword&gt; <I>all+</I>"<TT> may be required to locate a particular one.
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H3>Examples</H3>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. Find all help on CCDs.
  <P>
  	cl&gt; ref ccd
  <P>
  2. Create or update your private quick-reference file.
  <P>
  	cl&gt; ref upd+
  <P>
  3. Examine the quick-reference file to get a summary of all the tasks
  or other help modules in the help database.
  <P>
  	cl&gt; page (ref.quickref)
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H3>Time requirements</H3>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  If a quick-reference file is used searching takes seconds, otherwise it
  might take a minute or so for the typical large help database containing
  all help modules for the core system and several external, layered packages.
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H3>Bugs</H3>
  <! BeginSection: 'BUGS'>
  <UL>
  Only the one-liner (NAME) field describing each help module is used for
  the searches.  With a little work searching could be made much more
  comprehensive as well as faster.
  </UL>
  <! EndSection:   'BUGS'>
  <H3>See also</H3>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  help, match
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
