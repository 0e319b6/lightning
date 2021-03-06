lightning-checkmessage -- Command to check a signature is from a node
=====================================================================

SYNOPSIS
--------

**checkmessage** *message* *zbase* \[*pubkey*\]

DESCRIPTION
-----------

The **checkmessage** RPC command is the counterpart to
**signmessage**: given a node id (*pubkey*), signature (*zbase*) and a
*message*, it verifies that the signature was generated by that node
for that message (more technically: by someone who knows that node's
secret).

As a special case, if *pubkey* is not specified, we will try every
known node key (as per *listnodes*), and verification succeeds if it
matches for any one of them.  Note: this is implemented far more
efficiently than trying each one, so performance is not a concern.

RETURN VALUE
------------

On correct usage, an object with attribute *verified* will be
returned.

If *verified* is true, the signature was generated by the returned
*pubkey* for that given message.  *pubkey* is the one specified as
input, or if none was specified, the known node which must have
produced this signature.

If *verified* is false, the signature is meaningless.  *pubkey* may
also be returned, which is they *pubkey* (if any) for which this
signature would be valid.  This is usually not useful.

AUTHOR
------

Rusty Russell <<rusty@rustcorp.com.au>> is mainly responsible.

SEE ALSO
--------

lightning-signmessage(7)

RESOURCES
---------

Main web site: <https://github.com/ElementsProject/lightning>

