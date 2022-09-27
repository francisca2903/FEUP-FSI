
# Trabalho realizado na Semana #3

## Identificação

- File Deletion vulnerability allows the deletion of certain files which leads to certain privilege checks not being in place.
- This vulnerability targets the login system of the Automattic WooCommerce plugin before 3.4.6 version for WordPress.

## Catalogação

- The File Deletion vulnerability was reported to the WorldPress security team on Hackerone on November 20th 2017.
- This vulnerability was found and reported by the developer Karim El Ouerghemmi.
- It was also documented in the CVE platform and there was no bug-bounty. This bug has a high CVSS score of 8.1.
- 7 months after reporting, WordPress released a fixed version.

## Exploit

- If the attackers are able to delete certains plugins, they can disable the security checks and take over the site.
- This vulnerability can also be used to escalete privileges attained throught the takeover of an account.
- The weakness implies the use of external input to construct a pathname to a restricted directory.
- There is no automation. 

## Ataques

- There is no attack documented but as a possible one is by deleting the main file of WooCommerce.
- WordPress will be unable to load the plugin and then disables it.
- This vulnerability allows shop managers to delete any file on the server that is writable.
