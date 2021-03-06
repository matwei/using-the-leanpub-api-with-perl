## NAME

WebService::Leanpub - Access the Leanpub web API.

## VERSION

This document describes WebService::Leanpub version 0.3

## SYNOPSIS

    use WebService::Leanpub;

    my $wl = WebService::Leanpub->new($api_key, $slug);

    $wl->get_individual_purchases( { slug => $slug } );

    $wl->get_job_status( { slug => $slug } );

    $wl->preview();

    $wl->subset();

    $wl->get_sales_data( { slug => $slug } );

## DESCRIPTION

## INTERFACE 

### new($api\_key, $slug)

Create a new WebService::Leanpub object.

Since you need an API key to access any function of the Leanpub API, you have
to give that API key as an argument to `new()`.

The same holds for the _slug_ which is the part of the Leanpub URL denoting
your book. For instance if your books URL was
`https::/leanpub.com/your_book`, the slug woud be _your\_book_.

### get\_individual\_purchases()

### get\_individual\_purchases( $opt )

Get the data for individual purchases.

Optionally this method takes as argument a hash reference with this key:

- `page`

    the page of the individual purchases data.

### get\_job\_status()

Get the status of the last job.

### get\_sales\_data()

Get the sales data.

### partial\_preview()

Start a partial preview of your book using Subset.txt.

### subset()

Start a partial preview of your book using Subset.txt.

### preview()

Start a preview of your book.

### single( $opt )

Generate a preview of a single file.

The argument `$opt` is a hash reference with the following keys and values:

- content

    The content of the file in a scalar string.

### publish( $opt )

This will publish your book without emailing your readers.

The argument `$opt` is a hash reference with the following keys:

- email\_readers

    If the corresponding value evaluates to _true_, an email is sent to the
    readers.

- release\_notes

    The value corresponding to this key is sent as release note.

### create\_coupon( $opt )

Create a coupon.

The argument `$opt` is a hash reference with the following keys:

- coupon\_code

    Required.
    The coupon code for this coupon. This must be unique for the book.

- discounted\_price

    Required.
    The amount the reader will pay when using the coupon.

- start\_date

    Required.
    The date the coupon is valid from. Formatted like YYYY-MM-DD.

- end\_date

    The date the coupon is valid until. Formatted like YYYY-MM-DD.

- has\_uses\_limit

    Whether or not the coupon has a uses limit.

    Values '0', 'false', 'no' count as false, all other values as true.

- max\_uses

    The max number of uses available for a coupon. An integer.

- note

    A description of the coupon. This is just used to remind you of what it was
    for.

- suspended

    Whether or not the coupon is suspended.

    Values '0', 'false', 'no' count as false, all other values as true.

### update\_coupon( $opt )

Update a coupon.

Takes the same argumentes for `$opt`) as _create\_coupon()_ but only the key
`coupon_code` is required, all others are optional.

### get\_coupon\_list()

Returns a list of the coupons for the book formatted as JSON.

### pretty\_json( $json )

This is just a convenience function for pretty printing the output of the
`get_*()` functions.

### summary()

This returns information about the book.

Since this API function does not need an API key, this is the only method that
returns meaningful data if you provide a wrong API key.

## DIAGNOSTICS

- `Missing API key for Leanpub`

    Since the Leanpub API only works with an API key from leanpub.com, you have to
    provide an API key as first argument to WebService::Leanpub->new().

- `Missing SLUG for book`

    Since every action in the Leanpub API involves a book which is identified by a
    slug, you have to provide the slug as the second argument to
    WebService::Leanpub->new().

    A slug is the part after the hostname in the Leanpub URL of your book.
    For instance the book "Using the Leanpub API with Perl" has the URL
    [https://leanpub.com/using-the-leanpub-api-with-perl](https://leanpub.com/using-the-leanpub-api-with-perl) and the slug for
    this book is
    `using-the-leanpub-api-with-perl`.

## CONFIGURATION AND ENVIRONMENT

WebService::Leanpub requires no configuration files or environment variables.

## DEPENDENCIES

None.

## INCOMPATIBILITIES

None reported.

## BUGS AND LIMITATIONS

No bugs have been reported so far.

Please report any bugs or feature requests
through the web interface at [http://rt.cpan.org](http://rt.cpan.org)
or - if you prefer email - to `bug-webservice-leanpub@rt.cpan.org`.

## AUTHOR

Mathias Weidner  `<mamawe@cpan.org>`

## LICENCE AND COPYRIGHT

Copyright (c) 2013, Mathias Weidner `<mamawe@cpan.org>`. All rights reserved.

This module is free software; you can redistribute it and/or
modify it under the same terms as Perl itself. See [perlartistic](https://metacpan.org/pod/perlartistic).

## DISCLAIMER OF WARRANTY

BECAUSE THIS SOFTWARE IS LICENSED FREE OF CHARGE, THERE IS NO WARRANTY
FOR THE SOFTWARE, TO THE EXTENT PERMITTED BY APPLICABLE LAW. EXCEPT WHEN
OTHERWISE STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR OTHER PARTIES
PROVIDE THE SOFTWARE "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER
EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE
ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE SOFTWARE IS WITH
YOU. SHOULD THE SOFTWARE PROVE DEFECTIVE, YOU ASSUME THE COST OF ALL
NECESSARY SERVICING, REPAIR, OR CORRECTION.

IN NO EVENT UNLESS REQUIRED BY APPLICABLE LAW OR AGREED TO IN WRITING
WILL ANY COPYRIGHT HOLDER, OR ANY OTHER PARTY WHO MAY MODIFY AND/OR
REDISTRIBUTE THE SOFTWARE AS PERMITTED BY THE ABOVE LICENCE, BE
LIABLE TO YOU FOR DAMAGES, INCLUDING ANY GENERAL, SPECIAL, INCIDENTAL,
OR CONSEQUENTIAL DAMAGES ARISING OUT OF THE USE OR INABILITY TO USE
THE SOFTWARE (INCLUDING BUT NOT LIMITED TO LOSS OF DATA OR DATA BEING
RENDERED INACCURATE OR LOSSES SUSTAINED BY YOU OR THIRD PARTIES OR A
FAILURE OF THE SOFTWARE TO OPERATE WITH ANY OTHER SOFTWARE), EVEN IF
SUCH HOLDER OR OTHER PARTY HAS BEEN ADVISED OF THE POSSIBILITY OF
SUCH DAMAGES.
