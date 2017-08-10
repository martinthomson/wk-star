---
title: The 'star' Well-Known Resource for HTTP
abbrev: "WK*"
docname: draft-thomson-http-wk-star-latest
category: std

ipr: trust200902
area: ART
workgroup: HTTPBIS
keyword: Internet-Draft, HTTP, Well Known

stand_alone: yes

author:
 -
    ins: M. Thomson
    name: Martin Thomson
    organization: Mozilla
    email: martin.thomson@gmail.com


--- abstract

The asterisk-form of request target for HTTP is rarely used.  This document
defines a well-known resource that is equivalent to the asterisk-form target.

--- middle

# Introduction

HTTP defines the asterisk-form of a request target {{!HTTP=RFC7230}}.  This
form is limited in applicability to just the OPTIONS method {{?RFC7231}}.

Referring to a resource with the intent of using the asterisk-form is
challenging. Though the syntax of the http:// URI scheme permits the path to be
absent, and the asterisk-form is defined for use with an empty path for the
OPTIONS method, an empty path is equivalent to a path of "/" for all other
methods.  Consequently, it is common for software to erroneously convert a
request for a URI with an empty path to a request in origin-form and a path of
"/", even for the OPTIONS method.

This document defines a well-known resource {{!WELL-KNOWN=RFC5785}} that is
defined to be equivalent when used in origin- or absolute- form as a request
with the asterisk-form.

Defining a well-known resource allows the resource to be used more reliably.
It also provides a path for future versions of HTTP to remove support for the
asterisk-form.


# The "star" Well-Known URI

This document defines a well-known resource {{!WELL-KNOWN}} with a URI suffix
of "star".

An OPTIONS request to /.well-known/star on any HTTP server is defined to be
equivalent to an OPTIONS request that uses the asterisk-form.  The semantics
associated with other HTTP methods or other protocols is not defined.

Thus, an OPTIONS request to "https://example.com/.well-known/star" is equivalent
to an OPTIONS request to "https://example.com".


# Security Considerations

As with any other well-known resource, the intent of this resource is to
provide information that applies to the entire server.  As such, the security
considerations of {{!RFC5785}} apply.  Concerns about authority are mitigated
by the inherent limitations of a resource that purports to speak for the entire
server (see Section 4.3.7 of {{!RFC7231}} for details).


# IANA Considerations

IANA will register the "star" well-known resource in the "Well-Known URIs"
established in RFC 5785 {{!WELL-KNOWN}}.

URI Suffix:
: star

Change Controller:
: IETF

Reference:
: This document

Related Information:
: HTTP only.  An equivalent request target to the asterisk-form {{!HTTP}}.


--- back
