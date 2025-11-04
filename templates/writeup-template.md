# Room: <Room Name>

**Platform:** <TryHackMe / HackTheBox / Other>
**Category:** <Web / PrivEsc / Forensics / Crypto / etc.>
**Difficulty:** <Easy / Medium / Hard / ?/10>
**Target / Goal:** <What is the objective of the room?>

---

## TL;DR / Summary

A one-line summary of what you did and what you learned.

---

## 1) Environment / Notes

* Target IP / URL: `<REDACTED>` (use private file if you need real values)
* VM or persistent? `Yes / No / N/A`
* Tools I used: `nmap`, `gobuster`, `curl`, `ffuf`, `smbclient`, `msfconsole`, `linpeas`, `winpeas`, etc.
* Duration: `<time spent>`

---

## 2) Recon / Enumeration

**Commands I ran** (only include relevant snippets here; save full output to `outputs/`):

```bash
# Example nmap
nmap -sC -sV -p- -oN outputs/nmap-full.txt <TARGET>

# Example web dir brute
gobuster dir -u http://<TARGET> -w /path/to/wordlist -o outputs/gobuster.txt
```

**Key findings (short bullets):**

* Port 80 open -> HTTP (version / banner)
* Port 445 open -> SMB
* Hidden directory `/admin` discovered with gobuster

**Screenshots / Evidence:**
![Recon screenshot](images/01-recon.png)

Link to full outputs (kept in `outputs/`): `outputs/nmap-full.txt`, `outputs/gobuster.txt`

---

## 3) Initial Access / Exploitation

**Why I chose this approach** (explain your reasoning briefly):

**Steps / Commands**

```bash
# Example: curl to get web page
curl -s http://<TARGET>/admin | sed -n '1,120p'

# Example: Use Metasploit (redacted)
# msfconsole -q -x "use exploit/...; set RHOST <TARGET>; set LHOST <YOUR_IP>; run"
```

**What worked / what failed:**

* Method A produced a shell (describe type: reverse shell, meterpreter, web shell)
* Method B failed with error X — why I think it failed

**Screenshot / proof (redacted):**
![Exploit screenshot](images/02-exploit.png)

---

## 4) Foothold / Post-Exploitation

**Initial user context:**

* `whoami` -> `<username>`
* `id` / `hostname` / OS info: `<output here>`

**Commands used to explore the host:**

```bash
# Linux examples
uname -a
id
ps aux
sudo -l

# Windows examples (from shell)
whoami /priv
systeminfo
net user
ipconfig /all
```

**Interesting files / paths found:**

* `/home/<user>/notes.txt` (contains creds?)
* `C:\Program Files\SomeApp\service.exe` (unquoted path)

---

## 5) Privilege Escalation

**Enumeration for priv esc** (tools & commands):

* `linpeas.sh` / `winpeas.bat`
* `sudo -l`, `find / -perm -4000 -type f 2>/dev/null`

**Paths tried (ordered):**

1. Check sudoers / weak sudo privileges
2. Check SUID binaries / misconfigured services
3. Search for credentials stored in files or scripts
4. Check for unquoted service paths / weak permissions

**Method that worked (detailed steps):**

* Step 1: `<what you did>`
* Step 2: `<commands>`
* Step 3: `<result / why it gives escalated privileges>`

**Proof (redacted):**

* `root flag: FLAG{REDACTED}`

**Screenshot:**
![PrivEsc screenshot](images/03-privesc.png)

---

## 6) Final Notes / Cleanup

* Did you leave any tools or shells open? `Yes / No` — describe cleanup steps.
* Any artifacts you removed (only if safe and allowed by rules)

---

## 7) Lessons Learned

* Bullet 1: major technique learned
* Bullet 2: common pitfalls
* Bullet 3: further things to practice

---

## 8) Appendix (optional)

* Full `nmap` output: `outputs/nmap-full.txt`
* Full exploit output / logs: `outputs/exploit-stdout.txt`
* Raw screenshots (private): `private/` (add to `.gitignore`)

---

## 9) Redaction checklist (before publishing)

* [ ] Replace all real flags with `FLAG{REDACTED}` or `REDACTED_USER_FLAG_1`
* [ ] Remove or redact any real credentials (usernames/passwords)
* [ ] Ensure screenshots do not show flags (edit images or remove them)
* [ ] Add private proof files to `.gitignore`



