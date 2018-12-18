```
                     _.....---..._
      _..-'-.   _.--'             '--.._
  _.-' (  0) Y''                        ''-.._
 (---.._,                                     '-._
  `---.,___.-\  \----......./  /..------...____   '-.
     _/  /  _/  /         __\  \   __\  \      `-.   \
    (((-'  (((-'         (((---'  (((---`         )  /
                                               .-'.-'
    Chameleon: @domchell, MDSec ActiveBreach  (__`-,
               tChameleon fork: 07am             ``
```
# Description

Chameleon is a tool which assists red teams in categorising their infrastructure under arbitrary categories. Currently, the tool supports arbitrary categorisation for Bluecoat, McAfee Trustedsource and IBM X-Force. However, the tool is designed in such a way that additional proxies can be added with ease. tChamelon is a fork to add features to the original project.

# Usage

```
usage: tchameleon.py [-h] [--proxy <proxy>] [--check] [--submit] [--source <domain>]
                    [--domain <domain>]

optional arguments:
  -h, --help         show this help message and exit
  --proxy <proxy>    Proxy type: a = all, b = bluecoat, m = mcafee, i = IBM
                     Xforce
  --check            Perform check on current category
  --submit           Submit new category
  --domain <domain>  Domain to validate
  --source <domain>  Source to clone
```

Example 1: Checking the category of your website against all supported proxies:

```
$ python tchameleon.py --proxy a --check --domain google.com

                     _.....---..._
      _..-'-.   _.--'             '--.._
  _.-' (  0) Y''                        ''-.._
 (---.._,                                     '-._
  `---.,___.-\  \----......./  /..------...____   '-.
     _/  /  _/  /         __\  \   __\  \      `-.   \
    (((-'  (((-'         (((---'  (((---`         )  /
                                               .-'.-'
    Chameleon: @domchell, MDSec ActiveBreach  (__`-,
               tChameleon fork: 07am             ``

[-] Targeting Bluecoat WebPulse
[-] Checking category for google.com
[-] Your site is categorised as: Search Engines/Portals
[-] Targeting McAfee Trustedsource
[-] Getting anti-automation tokens
[-] Checking category for google.com
[-] Found category: - Search Engines
[-] Targeting IBM Xforce
[-] IBM xForce Check: google.com
[-] Domain categorised as Search Engines / Web Catalogues / Portals
```

Example 2: Submitting your domain for the financial category for BlueCoat proxy only:

```
$ python tchameleon.py --proxy b --submit --domain foobar.com --source https://www.wellsfargo.com

                     _.....---..._
      _..-'-.   _.--'             '--.._
  _.-' (  0) Y''                        ''-.._
 (---.._,                                     '-._
  `---.,___.-\  \----......./  /..------...____   '-.
     _/  /  _/  /         __\  \   __\  \      `-.   \
    (((-'  (((-'         (((---'  (((---`         )  /
                                               .-'.-'
    Chameleon: @domchell, MDSec ActiveBreach  (__`-,
               tChameleon fork: 07am             ``

[-] Getting anti-automation tokens
[-] Checking category for foobar.com
[-] Found category: - Personal Pages
[-] Submitting URL for finance category
```

**Caution**: when attempting to categorise a site in Bluecoat, do not check the category first otherwise it will end up uncategorised! Individual hosts can however be categorised differently.

# Credits

Chameleon was developed by [Dominic Chell](https://twitter.com/domchell) of the [MDSec ActiveBreach](https://www.mdsec.co.uk/services/red-teaming/) team.

Categorisation checks for Bluecoat and IBM X-Force were reused based on code originally developed in [DomainHunter](https://github.com/minisllc/domainhunter) and [CatMyFish](https://github.com/Mr-Un1k0d3r/CatMyFish).

Domain source and webroot check were added by [07am](https://github.com/07am).
