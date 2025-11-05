# Room: Search Skills

**Platform:** TryHackMe
**Category:** Web / OSINT
**Difficulty:** Easy
**Target / Goal:** Learn to efficiently search the Internet and use specialized search engines and technical docs

---

## TL;DR / Summary

Learned how to efficiently gather, evaluate, and verify information using advanced search techniques, specialized tools, and reliable online resources.

---

## 1) Introduction

Searching anything on the web can be tough. Indeed, a simple google research can return *millions* of results. The goal of this lesson is to acquire **search skills** to be more efficient finding and accessing what we are looking for.
We'll go through:
- evaluating information sources,
- using search engines efficiently,
- exploring specialized search engines,
- reading technical documentation,
- making use of social media,
- checking new outlets.

## 2) Evaluation of search results

As internet users, we know that anyone can write anything he wants on internet and this is our job to evaluate the information we're reading.
Here are few things to check when evaluating informations:
- **The source**: Can you identify the author or the organisation that gives the information? Are they  reputable and authoritative on the subject?
- **Evidence and reasoning**: Are the claims backed by clear evidence and logical reasonning? We need hard fact and solid arguments.
- **Objectivity and bias**: Is the information impartial and rationnal?
- **Corroboration and consistency**: You can only be sure of an information if the information is related by many sources. They need to be multiple, reliable and reputable. And of course, they need to agree on the central claim.

## 3) Search engines

Usually on search engines, rather that just typing the words/sentence we are searching, we can specify many thing.
We can use `"..."` to specify exact word or phrase. For example, use `"baguette au fromage"` to get pages with that exact phrase.
We can specify a domain name to specify the research using `site:`.
We can omit words of the research using the `-` symbol before the word we want to get.
We can do many many things to upgrade accuracy and they gives us a full list on that [github repository](https://github.com/cipher387/Advanced-search-operators-list).

## 4) Specialized search engines

Here knowledge start getting serious, they are introducing some specific search engines used to get specific types of results.
- First we are introduced to **Shodan** (visit [here](https://www.shodan.io)), that search engine can find any devices that are connected to the internet. It allow us to search for specific types and versions of servers, networking equipment, industrial control systems, and IoT devices.
To validate the stage we have to search which is the top country using `lighttpd` servers. (I let you go on Shodan with the link above to search for it by yourself!)
- There is also **Censys** (visit [here](https://search.censys.io)), which, at first glance, can look like **Shodan**. However, **Shodan** focuses on internet-connected devices and systems while **Censys** focuses on internet-connected hosts, certificates, and other Internet assets. Some of its use cases include enumerating domains in use, auditing open ports and services, and discovering rogue assets within a network. You can check all usages [here](https://docs.censys.com/docs/ls-introductory-use-cases#/).
- We also can use **VirusTotal** (visit [here](https://www.virustotal.com/gui/home/upload)) to scan any file, URL or hash to check wether they are infected or not by a malicious program. **VirusTotal** doesn't analyse the file itself but send it to many antivirus programs instead. Then the platform regroup all the results in a same place.
- Lastly they gave us **Have I Been Pwned** (visit [here](https://haveibeenpwned.com)), that website analyses if your email adress currently appears in leaked data breaches.

## 5) Vulnerabilities and exploits

##### CVE
There is a big program named Common Vulnerabilities and Exposures (CVE) used as a dictionnary of vulnerabilities. Each vulnerability gets a unique ID ensuring many people talking about the same one.

##### Exploit Database
There is plenty of reasons why you would exploit a vulnerable application, nevertheless remind it's absolutely forbidden to exploit any system unless getting the explicit authorization.
Many tools available on github are related to CVE.

## 6) Technical Documentation

There is many tools that get an official documentation, the most known for developpers remains the **Linux Manual Pages**. On Linux and every other Unix-like system, each command is expected to have a man page. There is also man pages for system calls, library functions and even configuration files.
Microsoft also provides an official documentation for its products.
And this is also expected for every popular product to get an official and well-organized documentation.

## 7) Social Media

Social media platforms like *Facebook*, *Twitter*, and *LinkedIn* are valuable sources of information and connection for cybersecurity professionals. They can be used to research people, gather intelligence, and stay updated on security trends and technologies. However, oversharing personal details online can expose users to **social engineering** or **account takeover** risks. When exploring new platforms, it’s best to use *temporary* email accounts to avoid linking activities to personal profiles. Following trusted cybersecurity groups and news outlets helps professionals stay informed and continuously improve their expertise.

---

## Conclusion

This room was a solid introduction to the foundations of effective online research and information gathering. I learned how to identify trustworthy sources, use advanced search operators to refine queries, and leverage specialized platforms such as Shodan, Censys, and VirusTotal to collect precise technical data. It also covered the importance of documentation, social media awareness, and cybersecurity news tracking for staying up to date. Overall, it provided a clear overview of how professionals can use the open web responsibly and efficiently to find valuable information.