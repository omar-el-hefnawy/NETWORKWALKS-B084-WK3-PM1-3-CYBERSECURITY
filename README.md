# NetworkWalks Internship — Week 3

Week 3 focused on password recovery in a controlled lab environment. The exercises used password-protected PDF files to demonstrate how a hash is extracted, how a password-cracking tool processes that hash, and how the recovered password is verified against the original document.

This repository covers both mandatory project modules and the optional AI-assisted exercise. All three were completed.

> **Lab-use note:** The techniques documented here were used with the training files and lab environment supplied for the NetworkWalks exercises. Only test files and systems you own or have explicit permission to assess.

The completed work covered:

- Project Module 1 — John the Ripper: Extracted a PDF hash, loaded it into Johnny, ran the cracking process, and checked the recovered password against the original PDF.
- Project Module 2 — NetworkWalks Tools: Used the NetworkWalks Hash Calculator to extract the PDF hash, then submitted it to the Password Cracker and verified the result.
- Optional — HexStrike MCP with Claude: Set up the HexStrike MCP server on Kali Linux, connected it to Claude Desktop, checked the local JTR installation, and used the connected tools for an AI-assisted cracking workflow.


For the first mandatory exercise, John the Ripper (JTR) and its graphical frontend, Johnny, were used on Windows.



The workflow was to install John the Ripper and Johnny, configure Johnny to use `john.exe` from the John installation's `run` directory, and extract a crackable hash from the supplied password-protected PDF. The extracted hash was saved in a text file and loaded into Johnny. A new attack was then started, and the recovered password was used to open the original PDF and confirm that it worked.

This exercise showed the distinction between extracting a hash and cracking it: Johnny processed the extracted hash, while opening the original PDF provided the final verification.






The supplied encrypted PDF was uploaded to the [NetworkWalks Hash Calculator](https://networkwalks.com/hash-calculator/) to extract its hash. The complete hash, including the `$pdf$` prefix, was copied and submitted to the [NetworkWalks Password Cracker](https://networkwalks.com/password-cracker/). After the tool returned a password, it was tested by opening the original PDF.


The optional exercise extended the JTR workflow by connecting Claude Desktop to HexStrike-AI through its MCP server, running in the Kali Linux lab environment.



Claude Desktop was installed on Kali using the [Claude Desktop Debian project](https://github.com/aaddrick/claude-desktop-debian). The [HexStrike-AI repository](https://github.com/0x4m4/hexstrike-ai) was cloned, a Python virtual environment was created and activated, and the dependencies listed in `requirements.txt` were installed. The server was started with `python3 hexstrike_server.py`.

Claude Desktop was then configured to connect to the local HexStrike MCP server at `http://localhost:8888`, using the Python interpreter from the HexStrike virtual environment and its MCP entry point.

With the connection established, Claude was used to check the server's health, confirm that John the Ripper was available, inspect the installed JTR version, extract the hash from the target PDF, and request a JTR attack using the `rockyou.txt` wordlist. The returned result was reviewed and the recovered password was checked against the PDF.

The MCP server exposed local tools to Claude through a standard interface. Claude provided the conversational way to request and review actions; John the Ripper still performed the actual cracking operation.


The main takeaways from the exercises were:

- Hash extraction and password cracking are separate steps. A cracking tool needs the hash in a format it supports.
- Dictionary attacks depend on the candidate passwords available in the selected wordlist. A successful match does not mean every password can be recovered this way.
- A recovered password should be tested against the original protected file.
- MCP can connect an AI client to local tools, but the underlying tools still perform the technical operations. Their results should be checked rather than accepted blindly.


Evidence

The screenshots below document the main steps and results from the three completed exercises.

**1. John the Ripper and Johnny**

*PDF hash extraction*

![JTR hash extraction](assets/screenshots/jtr-hash-extraction.png)

*Johnny cracking result*

![Johnny cracking result](assets/screenshots/johnny-cracking-result.png)

*JTR flag capture*

![JTR flag capture](assets/screenshots/flag-capture-jtr.png)


**2. NetworkWalks tools**

*Hash Calculator output*

![NetworkWalks Hash Calculator](assets/screenshots/nw-hash-calculator.png)

*Password Cracker result*

![NetworkWalks Password Cracker result](assets/screenshots/nw-password-cracker-result.png)

*NetworkWalks flag capture*

![NetworkWalks flag capture](assets/screenshots/flag-capture-networkwalks.png)


**3. HexStrike MCP and Claude Desktop**

*HexStrike server running on Kali Linux*

![HexStrike server startup](assets/screenshots/hexstrike-server-startup.png)

*Server health check and John the Ripper version*

![HexStrike health and JTR version](assets/screenshots/hexstrike-health-and-jtr-version.png)

*Claude-assisted hash extraction and cracking workflow*

![Claude JTR hash and crack](assets/screenshots/claude-jtr-hash-and-crack.png)

*Additional flag-capture confirmation*

![Flag capture persistence](assets/screenshots/flag-capture-persistence.png)


---

*NetworkWalks Cybersecurity Internship — Week 3*
