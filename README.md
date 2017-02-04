Grup is a perl script that was originally designed to report the
*up* status for a *Gr*oup of machines.  It has since mutated
into a versatile tool whose flexibility rivals *grep* even though
the names were purely coincidental.

In sprit with it's original design, grup with a single argument looks up
that argument as a YP netgroup (using ypmatch) and reports whether each
of the machines responds to a ping.

Without arguments, grup will tell you a little about what else it can
do:

    Usage: grup [-fnqs] [[-h hostname] ...] [netgroup] [-{e|r|p} commands]

	-e executes an sh command for each machine with any reference of %mx 
		translated to the remote machine name.
	-r is the same as -e with "ssh %mx" prepended
	-p is the same as -e but the command is evaluated as Perl 

	-h specifies a hostname to use (along with/instead of) the netgroup

	-f fork each command instead of running them sequentially
	-n shows the first up machine that returns
	-q only returns the output from the child processes
	-s only returns summary information 

	The default command if no -e is given is:
		ping -c %mx

