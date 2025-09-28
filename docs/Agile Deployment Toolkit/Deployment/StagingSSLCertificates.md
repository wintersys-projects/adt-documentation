There's two types of SSL certificates that can be issued. There's full certificates and there's staging certificates.

The staging certificates will give you a browser warning when you visit your site, something like, "This is not secure".

"Staging certificates" have no issuance limits where as "full certificates" do have issuance limits

To issue a live certificate set:

>     SSL_LIVE_CERT="1"

rather than

>     SSL_LIVE_CERT="0"

which will issue a staging certificate. 

NOTE: Staging certificates are only possible when using Letsencrypt they are not supported for Zerossl
