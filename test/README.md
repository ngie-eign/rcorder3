These directories contain test inputs and outputs common to all rcorder(8)
implementations: C, C++, and python.

From here on out, `$rcorder` shall refer to the rcorder program that is in
use. The implementations may have implementation specific behavior in terms of
the output, thus, `stdout`, `stderr`, etc, may be suffixed by `.c`, `.cc`, or
`.py`.

The general format for the testcase directories is as follows:

* `args`
  * Arguments to pass to `$rcorder`.
* `exit_status`
  * The expected exit status for `$rcorder` when executed with the mock input
    files.
* `files/*`
  * Mock input files to pass to `$rcorder`.
* `stderr`
  * Output printed to standard error.
* `stderr.$implementation`
  * Iimplementation-dependent output printed to standard error.
* `stdout`
  * Implementation-independent output printed to standard output.
* `stdout.$implementation`
  * Iimplementation-dependent output printed to standard output.
