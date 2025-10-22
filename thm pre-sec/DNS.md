Domain Name System provides a simple way to communicate with devices on the internet without remembering their IP addresses.

#### Domain Hierarchy

TLD (Top-Level Domain) is the most righthand part of a domain name, such as .com for example.
There are two types of TLD, gTLD (Generic Top Level) and ccTLD (Country Code Top Level Domain).
gTLD was meant to tell the user the domain name's purpose, for example .com would be for commercial purposes, .org for an organisation, .edu for education and .gov for government.
ccTLD was used for geographical purposes, for example .ca for sites based in Canada, .co.uk for sites based in the United Kingdom and so on.

Second-Level Domain is the actual name of the domain, when registering a domain name the second-level domain is limited to 63 characters + the TLD and can only use `a-z 0-9` and hyphens (but it cannot start or end with hyphens or have consecutive hyphens).

Subdomain sits on the left side of the Second-Level Domain using a period to separate it.
A subdomain name has the same creation restrictions as a Second-Level Domain which is also limited to 63 characters and can only use `a-z 0-9` and hyphens (same rules as the Second-Level Domain in regards to hyphens).
We can use multiple subdomain split with periods to created longer names `subdomain.domain.example.com` for example, but the length must be kept to 253 characters or less and there is no limit to the number of subdomains we can create for our domain name.

#### DNS Record Types

Common DNS records include:
* A Record - these records resolve to IPv4 addresses.
* AAAA Record - these records resolve to IPv6 addresses.
* CNAME Record - these records resolve to another domain name.
* MX Record - these records resolve to the address of the servers that handle the email for the domain we're querying.
* TXT Record - these are free text fields where any text-based data can be stored.

#### Requests

When we request a domain name our computer first checks its local cache to see if we've previously looked up the address before, if not, a request to our Recursive DNS Server will be made.
A recursive DNS Server is usually provided by our ISP but we could also choose our own.
This server also has a local cache of recently looked up domain names, if a result is found locally this is sent back to our computer and our request ends here.
The root servers act as the DNS backbone of the internet and their job is to redirect us to the correct Top Level Domain Server, depending on our request.
The TLD server holds records for where to find the authoritative server to answer the DNS request.
The authoritative server is often also known as the nameserver for the domain.
An authoritative DNS server is the server that is responsible for storing the DNS records for a particular domain name and where any updates to our domain name DNS records would be made.
Depending on the record type the DNS record is then sent back to the Recursive DNS Server where a local copy will be cached for future requests and then relayed back to the original client that made the request.
DNS records all come with a TTL value, this value is a number represented in seconds that the response should be saved for locally until we have to look it up again.
Caching saves on having to make a DNS request every time we communicate with a server.

