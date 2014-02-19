============
vmod_var
============

-----------------------------------------
Varnish Variable/Association List Module
-----------------------------------------

:Author: Tollef Fog Heen
:Date: 2011-09-28
:Version: 1.0
:Manual section: 3

SYNOPSIS
========

import var;

DESCRIPTION
===========

Association list in VCL. Can be used to mimick variables.

FUNCTIONS
=========

set_string
----------

Prototype
	set_string(STRING S, STRING T)
        set(STRING S, STRING T) - shorthand
Return value
	NONE
Description
	Sets the variable identified by S to the value T.
Example
	var.set_string("bar", "some random string");

get_string
----------

Prototype
	get_string(STRING S)
        get(STRING S) - shorthand
Return value
	STRING
Description
	Returns the string identified by the supplied string.
Example
	set resp.http.foo = var.get_string("bar");

Similar functions
-----------------

There are similar functions named:

* set_int(STRING, INT)
* get_int(STRING)
* set_real(STRING, REAL)
* get_real(STRING)
* set_duration(STRING, DURATION)
* get_duration(STRING)

get and set are shorthand for get_string and set_string.

del
-----

Prototype
	Function VOID del()
Returns
	NONE
Description
	Delete a variable. Does nothing if the variable
	doesn't exist.
Example
	var.del("state");

clear
-----

Prototype
	Function VOID clear()
Returns
	NONE
Description
	Clears out all the variables.
Example
	var.clear();

GLOBALS
=======

Global variables can be managed via the var.global_set,
var.global_get and var.global_del functions. All global values
must be strings.

global_set
----------

Prototype
	Function VOID global_set(STRING S, STRING T)
Returns
	NONE
Description
	Sets the global variable S to T (globals are visible
	for all sessions and requests).
Example
	var.global_set("state","active");

global_get
----------
Prototype
	Function STRING global_get(STRING S)
Returns
	STRING
Description
	Returns the global variable named S (globals are visible
	for all sessions and requests).
Example
	var.global_get("state");

global_del
----------
Prototype
	Function VOID global_del(STRING S)
Returns
	VOID
Description
	Deletes the global variable named S (globals are visible
	for all sessions and requests).
Example
	var.global_del("state");


HISTORY
=======

This manual page was written by Per Buer. It might contain
errors. Patches are welcome.

COPYRIGHT
=========

This document is licensed under the same license as the
libvmod-example project. See LICENSE for details.

* Copyright (c) 2012 Varnish Software
