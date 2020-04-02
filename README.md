# ConnectBoxDOCSIS-3.0

**Exploiting Connect Box EuroDOCSIS 3.0 Voice Gateway CH7465LG-NCIP-6.12.18.25-2p6-NOSH**

**CVE-2019-19967** - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-19967

**National Vulnerability Database - NVD** - https://nvd.nist.gov/vuln/detail/CVE-2019-19967

**Description**

The Administration page on Connect Box EuroDOCSIS 3.0 Voice Gateway CH7465LG-NCIP-6.12.18.25-2p6-NOSH devices accepts a cleartext password in a POST request on port 80, as demonstrated by the Password field to the xml/setter.xml URI. 

============================================================================

# ConnectBoxDOCSIS-3.0

![connect_box_1_modem](https://user-images.githubusercontent.com/31785433/71375371-48959d00-25be-11ea-99fc-6b23375f89c6.png)

The Connect Box is the worldwide most compact EuroDOCSIS 3.0 Voice Gateway which provides the ideal all-in-one wired and wireless solution, designed for your home, home office, or small business/enterprise.

It can be used in households with one or more computers capable of wireless connectivity for remote access to the wireless gateway.

============================================================================

The purpose of this exploration is to validate the security applied to the standard implementation of the router, as well as to guarantee the application of the main security models, whether in a home user or in a corporate environment.
We performed this proof of concept to get obtain the administrator credentials of the Connect Box DOCSIS 3.0 Voice Gateway router, it was possible to successfully perform, when sniffing the HTTP traffic packets, within the same tested network, when we perform some tests we discover a vulnerability in this router in the Authentication process known as Cleartext Transmission of Sensitive Information.
After discovering this flaw, we communicated the manufacturer about it, which put us in contact with the development team to assist in the improvement process, we also registered this failure through CVE - CVE-2019-19967 
Using Wireshark for packet capture and a Firefox browser to access the router management panel, it was possible to realize that admin credentials were passed in clear text, and not applied nothing of security, we could said the simple Basic Authentication (ie.Base64-encoded), as shown in the images below:

**Victim 1**

![Victim1](https://user-images.githubusercontent.com/31785433/71374644-bf7d6680-25bb-11ea-853f-44db27933398.png)

**Victim 2**

![Victim2](https://user-images.githubusercontent.com/31785433/71374789-534f3280-25bc-11ea-86a0-b6b16735e8c9.png)

**Attacker**

![Attacker](https://user-images.githubusercontent.com/31785433/71374788-534f3280-25bc-11ea-9b46-623b28997933.png)

**PoC in Video**

Here we can see three different Virtual Machines connecting in the same networking

**Access in the environment**

In this video below, We can see the all Attacker Machine using **Wireshark** to sniff the network, we realize two attempts to login in Administration page.

[![Access](https://i.vimeocdn.com/filter/overlay?src0=https%3A%2F%2Fi.vimeocdn.com%2Fvideo%2F841858314_1280x720.jpg&src1=https%3A%2F%2Ff.vimeocdn.com%2Fimages_v6%2Fshare%2Fplay_icon_overlay.png)](https://vimeo.com/381213952)

**WireShark**

Here, as we can see, we try acess with the password "admin", however we receive the "login incorrect", but when tha victim machine try to connect with the correct login, the wireshark receive the passaword in **clear text** as we can see.

[![Wiresharl](https://i.vimeocdn.com/filter/overlay?src0=https%3A%2F%2Fi.vimeocdn.com%2Fvideo%2F841858347_1280x720.jpg&src1=https%3A%2F%2Ff.vimeocdn.com%2Fimages_v6%2Fshare%2Fplay_icon_overlay.png)](https://vimeo.com/381213996)


**Pcap Analysis**

Here, we can see, a pcap file receive in kali linux machine, when we can open in the wireshark and we analyse this file, we can see the same behavior in about Authentication without simple protection.

[![Access](https://i.vimeocdn.com/filter/overlay?src0=https%3A%2F%2Fi.vimeocdn.com%2Fvideo%2F841858337_1280x720.jpg&src1=https%3A%2F%2Ff.vimeocdn.com%2Fimages_v6%2Fshare%2Fplay_icon_overlay.png)](https://vimeo.com/381213980)


**Manufacturer**

After discovering this flaw, we communicated(31/12/2020) the manufacturer about it, which put us in contact with the development team to assist in the improvement process (27/01/2020)
LASTUPDATE - 24/02/2020 by Manufacture
"What I can tell you is that this issue was discovered previously...but is hard to say when this will be fixed as the real vulnerability of this risk is very low"

**Publications** 

https://pentestmag.com/product/pentest-build-your-own-pentest-lab-in-2020/

https://www.linkedin.com/feed/update/urn:li:activity:6633366352042307585/


**References** 

https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-19967 

https://nvd.nist.gov/vuln/detail/CVE-2019-19967 

https://github.com/filipi86/ConnectBoxDOCSIS-3.0 

RFC 2660 - https://tools.ietf.org/html/rfc2660 

RFC 7231 - https://tools.ietf.org/html/rfc7231 

RFC 2818 - https://tools.ietf.org/html/rfc2818 

RFC 2612 - https://tools.ietf.org/html/rfc2616 

http://cwe.mitre.org/data/definitions/319.html 

Official Document form UPC  -  https://www.upc.ch/pdf/support/manuals/en/internet/ConnectBox/connect-box-manual.pdf  


