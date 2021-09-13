acatpars — Default astrometry file format parameter set
=======================================================

**Package: astcat**

.. raw:: html

  <BODY>
  <TABLE WIDTH="100%" BORDER=0><TR>
  <TD ALIGN=LEFT><FONT SIZE=4>
  <B>acatpars (Mar00)</B></FONT></TD>
  <TD ALIGN=CENTER><FONT SIZE=4>
  <B>astcat</B>
  </FONT></TD>
  <TD ALIGN=RIGHT><FONT SIZE=4>
  <B>acatpars (Mar00)</B></FONT></TD>
  </TR></TABLE><P>
  <TITLE>acatpars</TITLE>
  <UL>
  </UL>
  <H2><A NAME="s_name">NAME</A></H2>
  <! BeginSection: 'NAME'>
  <UL>
  acatpars -- edit the default astrometry file format parameters
  </UL>
  <! EndSection:   'NAME'>
  <H2><A NAME="s_usage">USAGE</A></H2>
  <! BeginSection: 'USAGE'>
  <UL>
  acatpars 
  </UL>
  <! EndSection:   'USAGE'>
  <H2><A NAME="s_parameters">PARAMETERS</A></H2>
  <! BeginSection: 'PARAMETERS'>
  <UL>
  <DL>
  <DT><B><A NAME="l_ftype">ftype = "<TT>stext</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ftype' Line='ftype = "stext"'>
  <DD>The astrometry file format. The current options are:
  <DL>
  <DT><B><A NAME="l_stext">stext</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='stext' Line='stext'>
  <DD>Simple text. Records are newline delimited and fields are whitespace delimited.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_btext">btext</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='btext' Line='btext'>
  <DD>Blocked text. Records are newline delimited and fields are offset and
  size delimited.
  </DD>
  </DL>
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ccsystem">ccsystem = "<TT>j2000</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='ccsystem' Line='ccsystem = "j2000"'>
  <DD>The default celestial coordinate system. The coordinate systems of most
  interest to users are "<TT>icrs</TT>", "<TT>j2000</TT>", and "<TT>b1950</TT>". For more detailed
  information on all the celestial coordinate system options type
  "<TT>help ccsystems</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_standard">standard astrometry file fields</A></B></DT>
  <! Sec='PARAMETERS' Level=0 Label='standard' Line='standard astrometry file fields'>
  <DD>The following parameters define the standard astrometry file fields. The
  parameter names are the same as the standard field names. The parameter
  values are the standard field descriptions.
  <BR>
  Every astrometry file returned by
  a catalog query or created by the user must contain the standard fields ra and
  dec. The remaining fields are optional and may or may not be present
  in either the original catalog or the astrometry file produced by a
  catalog query.
  <BR>
  The format of the standard fields is "<TT>fieldno [units [format]]</TT>" for simple
  text files and "<TT>foffset fsize [units [format]]</TT>" for blocked text files
  where the quantities in "<TT>[]</TT>" are optional. Standard fields with "<TT></TT>" valued
  field descriptions are assumed to be undefined.
  <BR>
  <DL>
  <DT><B><A NAME="l_id">id = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='id' Line='id = ""'>
  <DD>The standard id field. The data type is character. The default units and
  format values are "<TT>INDEF</TT>" and "<TT>%20s</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"> ra = "<TT>1 hours</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' ra = "1 hours"'>
  <DD>The standard right ascension / longitude field. The data type is double. The
  default units and format values are "<TT>hours</TT>"and "<TT>%11.2h</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"> dec = "<TT>2 degrees</TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' dec = "2 degrees"'>
  <DD>The standard declination / latitude field. The data type is double. The default
  units and format values are "<TT>degrees</TT>"and "<TT>%11.1h</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"> era = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' era = ""'>
  <DD>The standard right ascension / longitude error field. The data type is double.
  The default units and format values are "<TT>asecs</TT>" and "<TT>%6.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"> edec = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' edec = ""'>
  <DD>The standard declination / latitude error field. The data type is double.
  The default units and format values are "<TT>asecs</TT>" and "<TT>%6.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"> pmra = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' pmra = ""'>
  <DD>The standard right ascension / longitude proper motion field. The data type
  is double. The default units and format values are "<TT>masecs/yr</TT>" and "<TT>%7.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"> pmdec = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' pmdec = ""'>
  <DD>The standard declination / latitude proper motion field. The data type
  is double. The default units and format values are "<TT>masecs/yr</TT>" and "<TT>%7.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"> epmra = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' epmra = ""'>
  <DD>The standard right ascension / longitude proper motion error field. The data
  type is double. The default units and format values are "<TT>masecs/yr</TT>" and "<TT>%7.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_"> epmdec = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='' Line=' epmdec = ""'>
  <DD>The standard declination / latitude proper motion error field. The data
  type is double. The default units and format values are "<TT>masecs/yr</TT>" and "<TT>%7.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_catsystem">catsystem = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='catsystem' Line='catsystem = ""'>
  <DD>The standard celestial coordinate system field. The data type is character.
  The default units and format field values are "<TT>INDEF</TT>" and "<TT>%15s</TT>". If defined
  the value of this field overrides the coordinate system defined by the
  <I>csystem</I> parameter. Supported values of catsystem are "<TT>icrs</TT>", "<TT>fk5</TT>",
  "<TT>fk4</TT>", "<TT>fk4-noe</TT>", "<TT>ecliptic</TT>", "<TT>galactic</TT>", and "<TT>supergalactic</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_equinox">equinox = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='equinox' Line='equinox = ""'>
  <DD>The standard celestial coordinate system equinox field. The data type is
  character. The default units and format field values are "<TT>INDEF</TT>" and
  "<TT>%15s</TT>". Equinoxes are typical expressed as Julian epochs e.g. "<TT>J2000.0</TT>",
  Besselian epochs e.g. "<TT>B1950.0</TT>", or years "<TT>2000.0</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_epoch">epoch = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='epoch' Line='epoch = ""'>
  <DD>The standard celestial coordinate system epoch field. The data type is
  character. The default units and format field values are "<TT>INDEF</TT>" and
  "<TT>%15s</TT>". Epochs are typical expressed as Julian epochs e.g. "<TT>J2000.0</TT>",
  Besselian epochs e.g. "<TT>B1950.0</TT>", years "<TT>2000.0</TT>", or Julian date if the
  epoch value &gt; 3000.0.
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_px">px = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='px' Line='px = ""'>
  <DD>The standard parallax field. The data type is double. The default units
  and format values are "<TT>msecs</TT>" and "<TT>%6.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_rv">rv = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='rv' Line='rv = ""'>
  <DD>The standard radial velocity field. The data type is double. The default units
  and format values are "<TT>km/sec</TT>" and "<TT>%6.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_epx">epx = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='epx' Line='epx = ""'>
  <DD>The standard parallax error field. The data type is double. The default units
  and format values are "<TT>msecs</TT>" and "<TT>%6.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_erv">erv = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='erv' Line='erv = ""'>
  <DD>The standard radial velocity error field. The data type is double. The default
  units and format values are "<TT>km/sec</TT>" and "<TT>%6.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_mag">mag = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='mag' Line='mag = ""'>
  <DD>The standard magnitude field. The  data type is real. The default units
  and format field values are "<TT>mags</TT>" and "<TT>%8.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_color">color = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='color' Line='color = ""'>
  <DD>The standard color field. The  data type is real. The default units
  and format field values are "<TT>mags</TT>" and "<TT>%8.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_emag">emag = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='emag' Line='emag = ""'>
  <DD>The standard magnitude error field. The  data type is real. The default units
  and format field values are "<TT>mags</TT>" and "<TT>%8.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_ecolor">ecolor = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='ecolor' Line='ecolor = ""'>
  <DD>The standard color error field. The  data type is real. The default units
  and format field values are "<TT>mags</TT>" and "<TT>%8.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xp">xp = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xp' Line='xp = ""'>
  <DD>The predicted x coordinate field. The data type is double. The default units
  and format field values are "<TT>pixels</TT>" and "<TT>%9.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_yp">yp = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='yp' Line='yp = ""'>
  <DD>The predicted y coordinate field. The data type is double. The default units
  and format field values are "<TT>pixels</TT>" and "<TT>%9.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_xc">xc = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='xc' Line='xc = ""'>
  <DD>The centered x coordinate field. The data type is double. The default units
  and format field values are "<TT>pixels</TT>" and "<TT>%9.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_yc">yc = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='yc' Line='yc = ""'>
  <DD>The centered y coordinate field. The data type is double. The default units
  and format field values are "<TT>pixels</TT>" and "<TT>%9.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_exc">exc = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='exc' Line='exc = ""'>
  <DD>The centered x coordinate error field. The data type is double. The default
  units and format field values are "<TT>pixels</TT>" and "<TT>%9.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_eyc">eyc = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='eyc' Line='eyc = ""'>
  <DD>The centered y coordinate error field. The data type is double. The default
  units and format field values are "<TT>pixels</TT>" and "<TT>%9.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_imag">imag = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='imag' Line='imag = ""'>
  <DD>The standard instrumental magnitude field. The data type is real. The default
  units and format values are "<TT>mags</TT>" and "<TT>8.3f</TT>".
  </DD>
  </DL>
  <DL>
  <DT><B><A NAME="l_eimag">eimag = "<TT></TT>"</A></B></DT>
  <! Sec='PARAMETERS' Level=1 Label='eimag' Line='eimag = ""'>
  <DD>The standard instrumental magnitude error field. The data type is real. The
  default units and format values are "<TT>mags</TT>" and "<TT>8.3f</TT>".
  </DD>
  </DL>
  </DD>
  </DL>
  <P>
  </UL>
  <! EndSection:   'PARAMETERS'>
  <H2><A NAME="s_description">DESCRIPTION</A></H2>
  <! BeginSection: 'DESCRIPTION'>
  <UL>
  <P>
  The acatpars parameters define the default astrometry file format. These
  parameters are used if the input astrometry file does not contain a standard
  header describing the file format. By default standard headers are written
  by all astcat package tasks which create astrometry files. If the
  astrometry file does not have a header the acatpars parameters
  are used to define one.
  <P>
  By default acatpars assumes that the input astrometry file is a
  simple text file, <I>ftype</I> = "<TT>stext</TT>", with newline delimited records
  and whitespace delimited fields. In this case users can define
  the fields by setting the appropriate standard file parameters
  to a string with the following format, e.g.
  <P>
  <PRE>
  parname = "fieldno [units [format]]"
  <P>
       ra = "1 hours"
      dec = "2 degrees"
  </PRE>
  <P>
  where fieldno is the field or column number in the record. The
  units and format strings are optional and reasonable defaults are
  supplied if they are missing. Currently the units information is
  only used for decoding coordinate fields. For other fields the
  units should be left at their default values. The format information
  is used when an application has to decode a field into a numeric value
  modify it in some way and rewrite it.
  <P>
  If <I>ftype</I> is set to "<TT>btext</TT>" for blocked text the input astrometry file
  is assumed to be a text file with newline delimited records and fixed size
  fields. This format can be used to describe astrometry files with
  fields containing embedded blanks such as id fields. In this case users
  define the fields by setting the appropriate standard file parameters to
  a string with the following format, e.g.
  <P>
  <PRE>
  parname = "foffset fsize [units [format]]"
       ra = "1 15 hours"
      dec = "16 15 degrees"
  </PRE>
  <P>
  where foffset and fsize are the field offset and size in characters.
  Formats and units are treated in the same way as they for simple text files.
  <P>
  The fundamental coordinate system of the astrometry file is set by
  the <I>csystem</I> parameter. This is a global parameter applying to the
  entire astrometry file . Its value is overwritten if the "<TT>catsystem</TT>" standard
  field is defined, in which case the astrometry file may contain entries in
  many different fundamental coordinate systems.
  <P>
  </UL>
  <! EndSection:   'DESCRIPTION'>
  <H2><A NAME="s_examples">EXAMPLES</A></H2>
  <! BeginSection: 'EXAMPLES'>
  <UL>
  1. List the astrometry file format parameters.
  <P>
  <PRE>
  cl&gt; lpar acatpars
  </PRE>
  <P>
  2. Edit the astrometry file format parameters.
  <P>
  <PRE>
  cl&gt; acatpars
  </PRE>
  <P>
  3. Edit the astrometry file format parameters from the afiltcat task.
  <P>
  <PRE>
  cl&gt; epar afiltcat
  </PRE>
  <P>
  4. Save the current acatpars parameter values in a text file called
  acat1.par.  Use the saved parameter set in the next call to the afiltcat
  task.
  <P>
  <PRE>
  cl&gt; epar acatpars
  cl&gt; afiltcat ... acatpars=afilt1.par ...
  </PRE>
  <P>
  </UL>
  <! EndSection:   'EXAMPLES'>
  <H2><A NAME="s_time_requirements">TIME REQUIREMENTS</A></H2>
  <! BeginSection: 'TIME REQUIREMENTS'>
  <UL>
  </UL>
  <! EndSection:   'TIME REQUIREMENTS'>
  <H2><A NAME="s_bugs">BUGS</A></H2>
  <! BeginSection: 'BUGS'>
  <UL>
  </UL>
  <! EndSection:   'BUGS'>
  <H2><A NAME="s_see_also">SEE ALSO</A></H2>
  <! BeginSection: 'SEE ALSO'>
  <UL>
  afiltcat
  </UL>
  <! EndSection:    'SEE ALSO'>
  
  <! Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  >
  
  </BODY>
  </HTML>