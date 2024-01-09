# DNS
## Hierarchy
DNS follows a hierarchical structure. At the top of the hierarchy is the root domain, represented by a dot (.), followed by top-level domains (TLDs) like `.com`, `.net`, `.org`, and country-code TLDs like `.uk`, `.de`. Below these are second-level and further subdomains e.g. `.ost`, `.autoscout24`.
## Authoritative
An authoritative DNS server is one that has the original source data for a domain's Resource Records. It provides responses to queries about domains within its authority, usually hosted by the domain owner. These responses are considered definitive.
## Recursive
A recursive DNS query is one in which a DNS client asks a DNS server to fully resolve a domain name to an IP address. The recursive server will query other DNS servers on behalf of the client, managing the entire DNS query process until it returns the final answer back to the client.
## Iterative
In an iterative query, the DNS client allows the server to return its best answer. If the queried server does not have a match in its DNS cache or zone files, it will return a referral to a DNS server authoritative for a lower level of the domain hierarchy. The client then makes a query to this next server. This process is repeated until an answer is found or all possibilities are exhausted.
## Root
Root servers direct queries to the appropriate top-level domain (TLD) server, like .com, .net, or .org. They are crucial for the functioning of the global DNS system.
There are 13 root server clusters globally, labelled A through M, managed by various organizations and distributed worldwide for redundancy and stability.
## TTL
Time To Live is a value in a DNS record that indicates how long a resolver should cache the DNS query before the information becomes outdated and needs to be discarded. TTL is measured in seconds and the default is 12h (43200 seconds). 
## RRs
Resource Records are entries in a DNS zone file. They provide information about a domain, including its IP address (A record for IPv4, AAAA record for IPv6), mail servers (MX records), name servers (NS records), and other data like CNAME records for domain aliases or TXT records for various texts.
