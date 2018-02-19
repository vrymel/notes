# SendGrid whitelabel using TXT records in Namecheap

This is for doing a domain whitelabel in namecheap with the automatic security feature `off`.

Sendgrid will provide three DNS records to be configured in the domain provider, in this case Namecheap.

Notes when added the records in Namecheap.
* An `A Record` of the subdomain that points to the server must be configured
* In Namecheap, only use the subdomain part, here `parse`, as the value of the host in the TXT record
* Also, only use `m1.\_domainkey` as host in the `m1._domainkey.waypoints.direct` entry
* Wait atleast 30 minutes for the changes to propagate

Example record provided by SendGrid:

Type | Host | Data
--- | --- | ---
MX | parse.waypoints.direct | mx.sendgrid.net.
TXT | m1.\_domainkey.waypoints.direct | k=rsa; t=s; p=LONG\_STRING_REMOVED
TXT | parse.waypoints.direct | v=spf1 include:sendgrid.net ~all
