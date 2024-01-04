1. **Authoritative DNS Servers**:
    
    - **Definition**: These servers hold the complete and definitive data (records) for a domain.
    - **Function**: When a DNS query is made for a domain, the response from an authoritative server is considered final. It provides the exact answer if it has the information or a referral to other authoritative servers if it doesn't have the specific record.
    - **Data Storage**: They store DNS records such as A (address) records, MX (mail exchange) records, and others that are directly set by the domain's administrator.
2. **Recursive DNS Servers**:
    
    - **Definition**: These servers act as intermediaries between a client (like a web browser) and DNS servers. They are typically provided by ISPs or public DNS services.
    - **Function**: They receive DNS queries from clients and take on the task of finding the correct IP address. If they don't have the answer cached, they will query other DNS servers on behalf of the client.
    - **Process**: Recursive servers can perform a series of requests to various DNS servers to resolve the domain name into an IP address, which is then returned to the client.
3. **Iterative DNS Servers**:
    
    - **Definition and Function**: When a recursive server queries an iterative server, the iterative server responds with the best answer it can. If it does not have the exact match, it refers the recursive server to a closer authoritative server.
    - **Referral Process**: Instead of performing subsequent queries itself, an iterative server points the recursive server to another DNS server closer to the data.
4. **Root DNS Servers**:
    
    - **Definition**: These are the top-level DNS servers in the hierarchy.
    - **Function**: Root servers direct queries to the appropriate top-level domain (TLD) server, like .com, .net, or .org. They are crucial for the functioning of the global DNS system.
    - **Global Network**: There are 13 root server clusters globally, labeled A through M, managed by various organizations and distributed worldwide for redundancy and stability.

In summary:

- **Authoritative Servers** have the final answering authority over specific domains.
- **Recursive Servers** are the go-betweens for clients and other DNS servers, handling the full resolution process.
- **Iterative Servers** respond with referrals rather than performing additional queries.
- **Root Servers** are at the top of the DNS hierarchy, directing queries towards the appropriate TLD servers.