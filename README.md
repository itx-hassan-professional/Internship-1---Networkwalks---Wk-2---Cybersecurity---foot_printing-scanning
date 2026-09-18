<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>

<!-- TITLE -->
<h1>Penetration Testing Report</h1>
<h2>W2-P1 — Week 2 Report: Footprinting, Reconnaissance &amp; Network Scanning</h2>

<blockquote>
  <strong>Program:</strong> Networkwalks B082<br>
  <strong>Date:</strong> 11/9/2026<br>
  <strong>Modules Completed:</strong> W2-PM1(Multiple Kali Tools) & W2-PM5(Zenmap Scannig)<br>
  <strong>Client/Target:</strong> 1. Networkwalks(secured written permission already 2. My own local LAN Network <br>
  <strong>Permission secured from client?:</strong> yes <br>
  <strong>Phases covered:</strong> <b>Phase 1:</b> Reconnaissance & Footprinting <b>Phase 2:</b> Scanning & Network Discovery <br>
</blockquote>

<hr>

<!-- 1. DISCLAIMER -->
<h2>1. Liability Disclaimer</h2>
<div class="disclaimer">
  I have performed these activities only on the systems &amp; devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.
</div>

<hr>

<!-- 2. INTRODUCTION -->
<h2>2. Introduction</h2>
<p>
This report covers footprinting the <strong>networkwalks.com</strong> domain using multiple Kali Linux tools (W2-PM1) and scanning my own local network with Zenmap (W2-PM5). One module covers the footprinting phase and the other covers the scanning phase, so together they show how an attacker moves from gathering public information to mapping live hosts on a network. It is the Week 2 part of my ongoing internship program at Networkwalks.
</p>
<p>
All commands were run in <strong>Kali Linux</strong> (footprinting) and on a <strong>Windows PC with Zenmap installed</strong> (scanning). Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.
</p>

<hr>

<!-- 3. TOOLS USED -->
<h2>3. Tools Used</h2>
<p>The table below lists each tool used in this report and its purpose.</p>
<table>
  <thead>
    <tr><th>Tool</th><th>Purpose</th></tr>
  </thead>
  <tbody>
    <tr><td>Kali Linux &amp; Windows</td><td>Operating systems used for reconnaissance activities</td></tr>
    <tr><td>WHOIS</td><td>Find domain registration details (owner, dates, name servers).</td></tr>
    <tr><td>whatweb</td><td>Fingerprint web technologies (server, CMS, plugins, IP).</td></tr>
    <tr><td>nslookup</td><td>Resolve the domain name to its IP address using DNS.</td></tr>
    <tr><td>curl -I</td><td>Read the HTTP response headers of the website.</td></tr>
    <tr><td>wafw00f</td><td>Detect whether a Web Application Firewall protects the site.</td></tr>
    <tr><td>dnsrecon</td><td>Enumerate all DNS records (NS, MX, SPF, TXT, SRV).</td></tr>
    <tr><td>Zenmap (Nmap GUI)</td><td>Scan the local subnet to find live hosts, IPs and MAC addresses.</td></tr>
    <tr><td>Windows CMD</td><td>Local IP and MAC address identification</td></tr>
  </tbody>
</table>

<hr>

<!-- 4. ACTIVITIES PERFORMED -->
<h2>4. Activities Performed</h2>

<h3>4.1 Footprinting &amp; Reconnaissance</h3>
<p>
I performed reconnaissance against the <strong>networkwalks.com</strong> domain using six Kali Linux tools: <strong>WHOIS, WhatWeb, Nslookup, Curl, Wafw00f</strong> and <strong>DNSRecon</strong>. Each tool was used to collect a different type of information about the target.
</p>
<p>
First, I used <strong>WHOIS</strong> to obtain publicly available domain registration information and identify the domain's name servers. The results provided information about the domain registration and hosting infrastructure.
</p>
<p>
I then used <strong>WhatWeb</strong> to identify technologies used by the website. The results identified <strong>WordPress 7.1.1</strong> and <strong>WP Download Manager 3.3.58</strong>, along with other information exposed by the website.
</p>
<p>
Using <strong>Nslookup</strong>, I resolved the domain name to its IP address. The provided result identified <strong>192.232.216.135</strong>.
</p>
<p>
I used <strong>Curl</strong> with the <code>-I</code> option to inspect the HTTP response headers. This provided additional information about the web application and exposed the WordPress REST API endpoint <code>/wp-json/</code>.
</p>
<p>
Next, I used <strong>Wafw00f</strong> to determine whether a Web Application Firewall was protecting the website. The result identified <strong>ModSecurity (SpiderLabs)</strong>.
</p>
<p>
Finally, I used <strong>DNSRecon</strong> to enumerate DNS records. The results provided information relating to name servers, mail servers, SPF/TXT records, service records and DNS software information.
</p>

<h3>4.2 Network Scanning with Zenmap</h3>
<p>
For the second activity, I used <strong>Zenmap</strong> to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.
</p>
<p>
I first used the Windows <code>ipconfig</code> command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected <strong>Ping Scan</strong> to identify active hosts.
</p>
<p>The example results provided in the practical identified <strong>three live hosts</strong>:</p>
<ul>
  <li>10.15.98.2</li>
  <li>10.15.98.168</li>
  <li>10.15.98.47</li>
</ul>
<p>The example results also included <strong>four MAC addresses</strong>.</p>
<p>
After completing the scan, I opened the <strong>Topology</strong> section in Zenmap, enabled the legend and saved the network topology in <strong>PDF format</strong> as required by the practical task.
</p>
<blockquote>
  <strong>Note:</strong> The actual subnet, number of hosts and addresses should be replaced with the results from my own network when submitting the report.
</blockquote>

<hr>

<!-- 5. RISK ANALYSIS -->
<h2>5. Risk Analysis / Impact</h2>
<p>Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.</p>
<table>
  <thead>
    <tr>
      <th>#</th>
      <th>Risk / Finding</th>
      <th>Evidence / Observation</th>
      <th>Potential Impact</th>
      <th>Risk Level</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Web technology information exposed</td>
      <td>WhatWeb identified WordPress and WP Download Manager</td>
      <td>Attackers may use exposed technology/version information to identify software requiring further security review</td>
      <td class="risk-medium">Medium</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Server IP address identifiable</td>
      <td>Nslookup resolved the domain to 192.232.216.135</td>
      <td>Provides information about the network location of the web service</td>
      <td class="risk-low">Low</td>
    </tr>
    <tr>
      <td>3</td>
      <td>HTTP technical information exposed</td>
      <td>Curl returned HTTP response headers and exposed <code>/wp-json/</code></td>
      <td>May assist technology fingerprinting and further enumeration</td>
      <td class="risk-low">Low</td>
    </tr>
    <tr>
      <td>4</td>
      <td>WAF technology identifiable</td>
      <td>Wafw00f identified ModSecurity (SpiderLabs)</td>
      <td>Reveals information about the web application's security architecture</td>
      <td class="risk-low">Low</td>
    </tr>
    <tr>
      <td>5</td>
      <td>DNS infrastructure information exposed</td>
      <td>DNS Recon identified DNS, mail and service-related records</td>
      <td>DNS information can help build a broader infrastructure profile</td>
      <td class="risk-medium">Medium</td>
    </tr>
    <tr>
      <td>6</td>
      <td>Multiple live hosts visible on local network</td>
      <td>Zenmap identified four live hosts in the example network</td>
      <td>Unknown or unauthorized devices may potentially be present on a network</td>
      <td class="risk-medium">Medium</td>
    </tr>
  </tbody>
</table>
<p>
<strong>Risk level key:</strong>
<span class="risk-critical">🔴 Critical</span> ·
<span class="risk-medium">🟠 Medium</span> ·
<span class="risk-low">🟢 Low</span>
</p>
<p>
The risks above are observations from the footprinting and scanning exercises, <strong>not confirmed vulnerabilities</strong>.
</p>
<p>
The practical exercises primarily involved information gathering and host discovery. <strong>No exploitation or vulnerability validation</strong> was performed as part of these two modules.
</p>
<p>
Therefore, the presence of information such as a software version, IP address or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.
</p>

<hr>

<!-- 6. RECOMMENDATIONS -->
<h2>6. Recommendations</h2>
<p>Based on the observations from these activities, I recommend the following security improvements:</p>
<ol>
  <li><strong>Review publicly exposed technology information</strong> — Organizations should regularly review what information about their web technologies, CMS and plugins is publicly visible.</li>
  <li><strong>Keep software updated</strong> — CMS platforms, plugins and other web technologies should be regularly updated and reviewed against current security advisories.</li>
  <li><strong>Review HTTP headers</strong> — HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.</li>
  <li><strong>Review DNS records regularly</strong> — DNS records should be checked periodically to ensure that only required information and services are publicly exposed.</li>
  <li><strong>Properly configure and monitor the WAF</strong> — Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.</li>
  <li><strong>Perform regular internal network discovery</strong> — Organizations should periodically scan their own networks to identify active devices.</li>
  <li><strong>Investigate unknown devices</strong> — Any unexpected device discovered during network scanning should be investigated and verified.</li>
  <li><strong>Maintain network documentation</strong> — Network topology and device information should be documented and updated regularly.</li>
  <li><strong>Perform security testing with authorization</strong> — Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.</li>
</ol>

<hr>

<!-- 7. CONCLUSION -->
<h2>7. Conclusion</h2>
<p>
During <strong>Week 2</strong> of my Cybersecurity &amp; Ethical Hacking internship, I completed practical activities covering <strong>footprinting, reconnaissance and network scanning</strong>.
</p>
<p>
In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how <strong>WHOIS</strong> can provide domain information, <strong>WhatWeb</strong> can identify web technologies, <strong>Nslookup</strong> can resolve domain names, <strong>Curl</strong> can inspect HTTP headers, <strong>Wafw00f</strong> can identify a WAF, and <strong>DNSRecon</strong> can provide additional DNS information.
</p>
<p>
In the network scanning activity, I used <strong>Zenmap</strong> to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.
</p>
<p>
The exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.
</p>
<p>
I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk.
</p>
<p>
Finally, I learned that reconnaissance and scanning must always be performed <strong>within an authorized scope</strong>. These activities were completed as part of the assigned educational cybersecurity lab.
</p>

<hr>

<!-- END -->
<p class="center"><strong>— End —</strong></p>

<hr>

<!-- PROJECT INFORMATION -->
<h2>Project Information</h2>
<table class="author-table">
  <tr><td><strong>Author</strong></td><td>Waqas Karim — CCIE | Cybersecurity Professional (B082)</td></tr>
  <tr><td><strong>LinkedIn</strong></td><td><a href="https://www.linkedin.com/in/itxhassan" target="_blank">https://www.linkedin.com/in/itxhassan</a></td></tr>
  <tr><td><strong>Program Name</strong></td><td>Cybersecurity program at Networkwalks</td></tr>
  <tr><td><strong>Week</strong></td><td>02</td></tr>
  <tr><td><strong>Repository</strong></td><td>GitHub</td></tr>
</table>

</body>
</html>
