# Subnetting
## Classful 
Is superseded by Classless and CIDR subnetting.
Works by splitting a network into equally large subnets. either /8 /16 or /24
Example:
We have a network 172.16.0.0 with the subnet mask 255.255.0.0
And the following Subnets we need to create for a certain amount of hosts
- Switzerland 1000
- Iceland 340
- Norway 70
- Finland 40
- Sweden 3
For example 172.16.0.0  we would use class c (/24) but then we only have space for 256 hosts meaning it wont work :)

## Classless / CIDR
With Classless Inter-Domain Routing (CIDR), you're not restricted by class boundaries and can use a variable-length subnet mask (VLSM).

| Subnet ID | Subnet Address | Network ID | Host Address Range | Broadcast Address |
| ---- | :--: | :--: | :--: | :--: |
| Switzerland | 172.16.0.0/22 | 172.16.0.0 | 172.16.0.1 - 172.16.3.254 | 172.16.3.255 |
| Iceland | 172.16.4.0/23 | 172.16.4.0 | 172.16.4.1 - 172.16.5.254 | 172.16.5.255 |
| Norway | 172.16.6.0/25 | 172.16.6.0 | 172.16.6.1 - 172.16.6.126 | 172.16.6.127 |
| Finland | 172.16.6.128/26 | 172.16.6.128 | 172.16.6.129 - 172.16.6.190 | 172.16.6.191 |
| Sweden | 172.16.6.192/29<br> | 172.168.6.192 | 172.168.6.193 - 172.168.6.196 | 172.168.6.197 |
