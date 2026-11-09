# Hybrid connectivity

Ways to connect on-premises networks and other clouds to Google Cloud VPC networks: encrypted tunnels over the internet and private dedicated or partner links.

## Choosing an option

```mermaid
flowchart TD
  s["Connect another network"] --> q0{"Network in another<br/>cloud provider?"}
  q0 -->|"yes, high bandwidth"| cci["Cross-Cloud Interconnect (planned)"]
  q0 -->|"no, or low bandwidth"| q1{"Need more than a few Gbps<br/>or stable latency?"}
  q1 -->|no| vpn["Cloud VPN (HA VPN)"]
  q1 -->|yes| q2{"Presence in a supported<br/>colocation facility?"}
  q2 -->|yes| ded["Dedicated Interconnect"]
  q2 -->|no| par["Partner Interconnect"]
```

Start at the top: bandwidth and latency needs decide between the internet (VPN) and private links (Interconnect); physical presence decides between Dedicated and Partner.

## Notes in reading order

1. [Cloud VPN](cloud-vpn.md): IPsec tunnels, HA VPN, static and dynamic routing with Cloud Router.
2. [Cloud Interconnect](cloud-interconnect.md): Dedicated and Partner Interconnect, bandwidth, SLA and encryption.

## Planned topics

- Cloud Router and BGP in depth
- Cross-Cloud Interconnect
- Network Connectivity Center
- Direct Peering and Carrier Peering
- Hybrid DNS with Cloud DNS forwarding
