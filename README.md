PENETRATION TESTING REPORT

FOOTPRINTING & NETWORK SCANNING PHASES

W2-PM-FINAL | Cybersecurity Internship | NETWORKWALKS

| Pen tester Name (Cybersecurity Professional) | Abbas Ali Gedi |

| --- | --- |

| Program/Batch | B082 -- Networkwalks |

| Date | 20 August 2026 |

| Modules Completed | W2-PM4 (theHarvester) and W2-PM5 (Zenmap
Scanning) |

| Client/Target | 1. networkwalks.com (training/lab
target)<br>{=html}2. My own local Wi-Fi/LAN |

| Permission / Scope | Authorized training activity and scanning of my
own local network |

| Phases Covered | Phase 1: Reconnaissance &
Footprinting<br>{=html}Phase 2: Scanning & Network Discovery |

Liability Disclaimer

I performed these activities only against the authorized training target
and devices/network resources that I own. The work is for educational
and cybersecurity research purposes only. No exploitation, credential
attacks, persistence, or destructive actions were performed.
Unauthorized access or scanning may be illegal; therefore, the
techniques in this report must only be used within an explicitly
authorized scope.

2. Introduction

This report documents two Week 2 practical activities. First,
theHarvester was used from Kali Linux to perform passive footprinting of
the networkwalks.com training domain. Second, Nmap/Zenmap was used from
a Windows machine to discover hosts on my own local Wi-Fi network and
generate a topology view. The evidence shows the commands, observed
results, limitations, and security relevance of the findings.

3. Tools Used

| Tool | Purpose |

| --- | --- |

| Kali Linux | Operating system used for theHarvester reconnaissance
activity. |

| theHarvester 4.10.1 | Collect public-domain information such as
emails, IPs, hosts, subdomains and related infrastructure. |

| Zenmap / Nmap 7.991 | Discover live hosts, identify open ports and
visualize network topology on the local LAN. |

| Windows CMD / ipconfig | Identify local network interface
configuration and the subnet used for scanning. |

4.1 OSINT Footprinting & Reconnaissance

I performed passive reconnaissance using theHarvester 4.10.1 in Kali
Linux against the authorized target networkwalks.com.

Step 1: Baidu Search

I first used Baidu as the search source:

theHarvester -d networkwalks.com -l 1000 -b baidu

The scan returned 0 IPs, 0 emails, 0 people, and 0 hosts.

Step 2: Multiple Sources

I then performed a broader search using all available sources:

theHarvester -d networkwalks.com -l 50 -b all

The scan identified 3 ASNs, 2 URLs, 1 email address, IP information, and
32 hosts/subdomains.

Step 3: Review Results

I reviewed and documented the collected information. Some sources
required API keys, so not every available source returned results.

Step 4: Evidence

Screenshots of theHarvester commands and results were collected and
included as evidence in this report.

This activity demonstrated how OSINT techniques can be used to identify
publicly available information about a target without attempting
unauthorized access.

4.2 Network Scanning with Zenmap

For the second practical activity, I scanned my own local Wi-Fi/LAN. The
Windows ipconfig command was used first to identify the local interface
and network range. Sensitive local IP and MAC values have been masked in
the evidence images included in this report.

Observed local network: 10.xx.xx.0/24 (sensitive address values masked
in evidence).

Step 1: Identify local network configuration

Command: ipconfig /all

The command displayed the Windows Wi-Fi adapter, IPv4 configuration,
subnet mask, default gateway, DHCP/DNS information and hardware address.
These values were used only to determine the local scanning scope.

Command: ipconfig

The shorter ipconfig output confirmed the local Wi-Fi IPv4 configuration
and the /24 subnet used for the discovery scan.

Step 2: Zenmap / Nmap host discovery and service scan

Scan result: 3 hosts were up on the scanned 256-address range.

The Nmap result identified three live hosts. One host exposed DNS on
TCP/53, while the Windows host exposed TCP/135, TCP/139, TCP/445 and
TCP/7070. The report evidence masks the local IP addresses and preserves
the topology structure.

| Host role (masked) | Observed ports | Observation |

| --- | --- | --- |

| Host A (masked) | No open ports shown; 100 scanned ports were
closed/ignored | Host was reachable but did not expose an open TCP
service in the reported scan. |

| Host B (masked) | 53/tcp -- domain | DNS service was reachable on
TCP/53. |

| Host C (masked) | 135/tcp -- msrpc; 139/tcp -- netbios-ssn; 445/tcp
-- microsoft-ds; 7070/tcp -- realserver | Windows-related services
and an additional service were reachable and should be reviewed on an
owned system. |

5. Risk Analysis / Impact

The following are observations from the footprinting and internal
host-discovery exercises. They are not confirmed vulnerabilities. No
exploitation or vulnerability validation was performed.

| Risk | Level | Evidence | Potential impact |

| --- | --- | --- | --- |

| Public email exposure | Medium | info@networkwalks.com was returned.
| May support phishing or social engineering if not protected by
other controls. |

| Large public host/subdomain footprint | Medium | 32 host/subdomain
entries were reported. | More externally visible endpoints may
increase the attack surface. |

| DNS service on local host | Low--Medium | TCP/53 was open on one
discovered local host. | An exposed service should be intentional,
patched and restricted to required clients. |

| SMB/NetBIOS services on local Windows host | Medium | TCP/139 and
TCP/445 were open. | These services should be limited to trusted
networks and kept patched to reduce lateral-movement risk. |

6. Recommendations

Reduce public information exposure --- Review public contact
information and use controlled contact mechanisms where appropriate
to reduce phishing exposure.

Review public subdomains --- Confirm that cPanel, FTP, mail, webmail
and related endpoints are required. Restrict administrative services
and enforce strong authentication.

Harden local Windows services --- Review TCP/135, TCP/139 and
TCP/445 on the Windows host. Disable unused services and maintain
current security patches.

Restrict DNS exposure --- Confirm that TCP/53 is required on the
discovered host and restrict DNS service access to authorized
clients.

Maintain an internal asset inventory --- Regularly scan the owned
LAN to identify unknown or unauthorized devices.

Protect network documentation --- Keep IP addresses, MAC addresses
and topology diagrams private. The screenshots in this report
intentionally mask those local identifiers.

Scan only within authorization --- Continue performing
reconnaissance and scanning only against authorized targets or
systems owned by the tester.

7. Conclusion

During Week 2 of the Cybersecurity & Ethical Hacking program, I
completed practical activities covering footprinting, reconnaissance and
network scanning. Using theHarvester, I collected public information
associated with networkwalks.com, including an email address, IP
information, ASNs, URLs and a set of host/subdomain records. The
exercise also demonstrated that reconnaissance results depend on the
availability and authentication requirements of individual data sources.

Using Zenmap/Nmap on my own local Wi-Fi network, I identified three live
hosts and observed several reachable services. I also generated a
topology showing the relationships between the discovered nodes. The
exercise reinforced that network discovery should be performed carefully
and within a defined scope.

Finally, I learned that a professional security report should document
the command used, the evidence obtained, the meaning of the observation,
the potential security impact and practical recommendations. Local IP
and MAC identifiers were masked in this report to protect the privacy of
the local network.

--- End ---

Author Abbas Ali Gedi Cybersecurity & Ethical hacking internship at
Network walks -- B082

Program Name: Cybersecurity program at Networkwalks | Week: 02
| Repository: GitHub

Evidence Images









