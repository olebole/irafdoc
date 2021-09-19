.. _acatpars:

acatpars: Default astrometry file format parameter set
======================================================

**Package: astcat**

.. raw:: html

  </tr></table><p>
  <h3>Name</h3>
  <!-- BeginSection: 'NAME' -->
  <p>
  acatpars -- edit the default astrometry file format parameters
  </p>
  <!-- EndSection:   'NAME' -->
  <h3>Usage</h3>
  <!-- BeginSection: 'USAGE' -->
  <p>
  acatpars 
  </p>
  <!-- EndSection:   'USAGE' -->
  <h3>Parameters</h3>
  <!-- BeginSection: 'PARAMETERS' -->
  <dl>
  <dt><b>ftype = <tt>"stext"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ftype' Line='ftype = "stext"' -->
  <dd>The astrometry file format. The current options are:
  <dl>
  <dt><b>stext</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='stext' Line='stext' -->
  <dd>Simple text. Records are newline delimited and fields are whitespace delimited.
  </dd>
  </dl>
  <dl>
  <dt><b>btext</b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='btext' Line='btext' -->
  <dd>Blocked text. Records are newline delimited and fields are offset and
  size delimited.
  </dd>
  </dl>
  </dd>
  </dl>
  <dl>
  <dt><b>ccsystem = <tt>"j2000"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='ccsystem' Line='ccsystem = "j2000"' -->
  <dd>The default celestial coordinate system. The coordinate systems of most
  interest to users are <tt>"icrs"</tt>, <tt>"j2000"</tt>, and <tt>"b1950"</tt>. For more detailed
  information on all the celestial coordinate system options type
  <tt>"help ccsystems"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>standard astrometry file fields</b></dt>
  <!-- Sec='PARAMETERS' Level=0 Label='standard' Line='standard astrometry file fields' -->
  <dd>The following parameters define the standard astrometry file fields. The
  parameter names are the same as the standard field names. The parameter
  values are the standard field descriptions.
  <br>
  Every astrometry file returned by
  a catalog query or created by the user must contain the standard fields ra and
  dec. The remaining fields are optional and may or may not be present
  in either the original catalog or the astrometry file produced by a
  catalog query.
  <br>
  The format of the standard fields is <tt>"fieldno [units [format]]"</tt> for simple
  text files and <tt>"foffset fsize [units [format]]"</tt> for blocked text files
  where the quantities in <tt>"[]"</tt> are optional. Standard fields with <tt>""</tt> valued
  field descriptions are assumed to be undefined.
  <br>
  <dl>
  <dt><b>id = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='id' Line='id = ""' -->
  <dd>The standard id field. The data type is character. The default units and
  format values are <tt>"INDEF"</tt> and <tt>"%20s"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b> ra = <tt>"1 hours"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line=' ra = "1 hours"' -->
  <dd>The standard right ascension / longitude field. The data type is double. The
  default units and format values are <tt>"hours"</tt>and <tt>"%11.2h"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b> dec = <tt>"2 degrees"</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line=' dec = "2 degrees"' -->
  <dd>The standard declination / latitude field. The data type is double. The default
  units and format values are <tt>"degrees"</tt>and <tt>"%11.1h"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b> era = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line=' era = ""' -->
  <dd>The standard right ascension / longitude error field. The data type is double.
  The default units and format values are <tt>"asecs"</tt> and <tt>"%6.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b> edec = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line=' edec = ""' -->
  <dd>The standard declination / latitude error field. The data type is double.
  The default units and format values are <tt>"asecs"</tt> and <tt>"%6.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b> pmra = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line=' pmra = ""' -->
  <dd>The standard right ascension / longitude proper motion field. The data type
  is double. The default units and format values are <tt>"masecs/yr"</tt> and <tt>"%7.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b> pmdec = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line=' pmdec = ""' -->
  <dd>The standard declination / latitude proper motion field. The data type
  is double. The default units and format values are <tt>"masecs/yr"</tt> and <tt>"%7.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b> epmra = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line=' epmra = ""' -->
  <dd>The standard right ascension / longitude proper motion error field. The data
  type is double. The default units and format values are <tt>"masecs/yr"</tt> and <tt>"%7.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b> epmdec = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='' Line=' epmdec = ""' -->
  <dd>The standard declination / latitude proper motion error field. The data
  type is double. The default units and format values are <tt>"masecs/yr"</tt> and <tt>"%7.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>catsystem = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='catsystem' Line='catsystem = ""' -->
  <dd>The standard celestial coordinate system field. The data type is character.
  The default units and format field values are <tt>"INDEF"</tt> and <tt>"%15s"</tt>. If defined
  the value of this field overrides the coordinate system defined by the
  <i>csystem</i> parameter. Supported values of catsystem are <tt>"icrs"</tt>, <tt>"fk5"</tt>,
  <tt>"fk4"</tt>, <tt>"fk4-noe"</tt>, <tt>"ecliptic"</tt>, <tt>"galactic"</tt>, and <tt>"supergalactic"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>equinox = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='equinox' Line='equinox = ""' -->
  <dd>The standard celestial coordinate system equinox field. The data type is
  character. The default units and format field values are <tt>"INDEF"</tt> and
  <tt>"%15s"</tt>. Equinoxes are typical expressed as Julian epochs e.g. <tt>"J2000.0"</tt>,
  Besselian epochs e.g. <tt>"B1950.0"</tt>, or years <tt>"2000.0"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>epoch = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='epoch' Line='epoch = ""' -->
  <dd>The standard celestial coordinate system epoch field. The data type is
  character. The default units and format field values are <tt>"INDEF"</tt> and
  <tt>"%15s"</tt>. Epochs are typical expressed as Julian epochs e.g. <tt>"J2000.0"</tt>,
  Besselian epochs e.g. <tt>"B1950.0"</tt>, years <tt>"2000.0"</tt>, or Julian date if the
  epoch value &gt; 3000.0.
  </dd>
  </dl>
  <dl>
  <dt><b>px = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='px' Line='px = ""' -->
  <dd>The standard parallax field. The data type is double. The default units
  and format values are <tt>"msecs"</tt> and <tt>"%6.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>rv = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='rv' Line='rv = ""' -->
  <dd>The standard radial velocity field. The data type is double. The default units
  and format values are <tt>"km/sec"</tt> and <tt>"%6.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>epx = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='epx' Line='epx = ""' -->
  <dd>The standard parallax error field. The data type is double. The default units
  and format values are <tt>"msecs"</tt> and <tt>"%6.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>erv = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='erv' Line='erv = ""' -->
  <dd>The standard radial velocity error field. The data type is double. The default
  units and format values are <tt>"km/sec"</tt> and <tt>"%6.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>mag = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='mag' Line='mag = ""' -->
  <dd>The standard magnitude field. The  data type is real. The default units
  and format field values are <tt>"mags"</tt> and <tt>"%8.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>color = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='color' Line='color = ""' -->
  <dd>The standard color field. The  data type is real. The default units
  and format field values are <tt>"mags"</tt> and <tt>"%8.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>emag = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='emag' Line='emag = ""' -->
  <dd>The standard magnitude error field. The  data type is real. The default units
  and format field values are <tt>"mags"</tt> and <tt>"%8.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>ecolor = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='ecolor' Line='ecolor = ""' -->
  <dd>The standard color error field. The  data type is real. The default units
  and format field values are <tt>"mags"</tt> and <tt>"%8.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>xp = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='xp' Line='xp = ""' -->
  <dd>The predicted x coordinate field. The data type is double. The default units
  and format field values are <tt>"pixels"</tt> and <tt>"%9.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>yp = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='yp' Line='yp = ""' -->
  <dd>The predicted y coordinate field. The data type is double. The default units
  and format field values are <tt>"pixels"</tt> and <tt>"%9.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>xc = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='xc' Line='xc = ""' -->
  <dd>The centered x coordinate field. The data type is double. The default units
  and format field values are <tt>"pixels"</tt> and <tt>"%9.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>yc = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='yc' Line='yc = ""' -->
  <dd>The centered y coordinate field. The data type is double. The default units
  and format field values are <tt>"pixels"</tt> and <tt>"%9.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>exc = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='exc' Line='exc = ""' -->
  <dd>The centered x coordinate error field. The data type is double. The default
  units and format field values are <tt>"pixels"</tt> and <tt>"%9.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>eyc = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='eyc' Line='eyc = ""' -->
  <dd>The centered y coordinate error field. The data type is double. The default
  units and format field values are <tt>"pixels"</tt> and <tt>"%9.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>imag = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='imag' Line='imag = ""' -->
  <dd>The standard instrumental magnitude field. The data type is real. The default
  units and format values are <tt>"mags"</tt> and <tt>"8.3f"</tt>.
  </dd>
  </dl>
  <dl>
  <dt><b>eimag = <tt>""</tt></b></dt>
  <!-- Sec='PARAMETERS' Level=1 Label='eimag' Line='eimag = ""' -->
  <dd>The standard instrumental magnitude error field. The data type is real. The
  default units and format values are <tt>"mags"</tt> and <tt>"8.3f"</tt>.
  </dd>
  </dl>
  </dd>
  </dl>
  <!-- EndSection:   'PARAMETERS' -->
  <h3>Description</h3>
  <!-- BeginSection: 'DESCRIPTION' -->
  <p>
  The acatpars parameters define the default astrometry file format. These
  parameters are used if the input astrometry file does not contain a standard
  header describing the file format. By default standard headers are written
  by all astcat package tasks which create astrometry files. If the
  astrometry file does not have a header the acatpars parameters
  are used to define one.
  </p>
  <p>
  By default acatpars assumes that the input astrometry file is a
  simple text file, <i>ftype</i> = <tt>"stext"</tt>, with newline delimited records
  and whitespace delimited fields. In this case users can define
  the fields by setting the appropriate standard file parameters
  to a string with the following format, e.g.
  </p>
  <pre>
  parname = "fieldno [units [format]]"
  
       ra = "1 hours"
      dec = "2 degrees"
  </pre>
  <p>
  where fieldno is the field or column number in the record. The
  units and format strings are optional and reasonable defaults are
  supplied if they are missing. Currently the units information is
  only used for decoding coordinate fields. For other fields the
  units should be left at their default values. The format information
  is used when an application has to decode a field into a numeric value
  modify it in some way and rewrite it.
  </p>
  <p>
  If <i>ftype</i> is set to <tt>"btext"</tt> for blocked text the input astrometry file
  is assumed to be a text file with newline delimited records and fixed size
  fields. This format can be used to describe astrometry files with
  fields containing embedded blanks such as id fields. In this case users
  define the fields by setting the appropriate standard file parameters to
  a string with the following format, e.g.
  </p>
  <pre>
  parname = "foffset fsize [units [format]]"
       ra = "1 15 hours"
      dec = "16 15 degrees"
  </pre>
  <p>
  where foffset and fsize are the field offset and size in characters.
  Formats and units are treated in the same way as they for simple text files.
  </p>
  <p>
  The fundamental coordinate system of the astrometry file is set by
  the <i>csystem</i> parameter. This is a global parameter applying to the
  entire astrometry file . Its value is overwritten if the <tt>"catsystem"</tt> standard
  field is defined, in which case the astrometry file may contain entries in
  many different fundamental coordinate systems.
  </p>
  <!-- EndSection:   'DESCRIPTION' -->
  <h3>Examples</h3>
  <!-- BeginSection: 'EXAMPLES' -->
  <p>
  1. List the astrometry file format parameters.
  </p>
  <pre>
  cl&gt; lpar acatpars
  </pre>
  <p>
  2. Edit the astrometry file format parameters.
  </p>
  <pre>
  cl&gt; acatpars
  </pre>
  <p>
  3. Edit the astrometry file format parameters from the afiltcat task.
  </p>
  <pre>
  cl&gt; epar afiltcat
  </pre>
  <p>
  4. Save the current acatpars parameter values in a text file called
  acat1.par.  Use the saved parameter set in the next call to the afiltcat
  task.
  </p>
  <pre>
  cl&gt; epar acatpars
  cl&gt; afiltcat ... acatpars=afilt1.par ...
  </pre>
  <!-- EndSection:   'EXAMPLES' -->
  <h3>Time requirements</h3>
  <!-- BeginSection: 'TIME REQUIREMENTS' -->
  <!-- EndSection:   'TIME REQUIREMENTS' -->
  <h3>Bugs</h3>
  <!-- BeginSection: 'BUGS' -->
  <!-- EndSection:   'BUGS' -->
  <h3>See also</h3>
  <!-- BeginSection: 'SEE ALSO' -->
  <p>
  afiltcat
  </p>
  
  <!-- EndSection:    'SEE ALSO' -->
  
  <!-- Contents: 'NAME' 'USAGE' 'PARAMETERS' 'DESCRIPTION' 'EXAMPLES' 'TIME REQUIREMENTS' 'BUGS' 'SEE ALSO'  -->
  
