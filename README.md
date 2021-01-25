# About this repository

This is an input source of the Ultimate Hosts Blacklist project.
Its objective is to test and provide a cleaned version the upstream list.

## Understanding the structure

### `.pyfunceble` directory

The `.pyfunceble` directory is the directory that PyFunceble consider as its
configuration directory.
In other words, it is where PyFunceble stores everything that has nothing to
do with the test results.

### `output` directory

The `output` directory is the directory where the results of the execution of
PyFunceble is stored until a test is complete (all subjects tested).

### `info.json`

The `info.json` file is interpreted by our launcher. It describes the
input source to work with, where to fetch it and when we fetch it.

### `clean.list` file

The `clean.list` file contains all `ACTIVE` results of
PyFunceble.

### `domains.list` file

The `domains.list` file contains the decoded version of the upstream list.

### `ip.list` file

The `ip.list` file contains all `ACTIVE` IP tested by PyFunceble.

### `volatile.list` file

The `volatile.list` file contains the content of the `clean.list` file + the
list of subjects which were flagged by the SPECIAL rules of PyFunceble as
`ACTIVE`.

### `whitelisted.list` file

The `whitelisted.list` file contains the content of the `clean.list` file
without all our whitelisted subjects.


# About Ultimate Hosts Blacklist

The [Ultimate Hosts Blacklist](https://github.com/ultimate-hosts-blacklist/ultimate.hosts.blacklist) project is undoubtedly one of the world's
largest curated Unified Hosts file for protecting your network, computer,
device, children, or family against over several hundred thousand malicious
actors.

The Ultimate Hosts Blacklist differentiates itself from other similar projects
because of the usage of PyFunceble in order to distribute as much `ACTIVE`
subject as possible while continuously retesting all `INACTIVE` subjects.


# About PyFunceble

[PyFunceble](https://github.com/funilrys/PyFunceble) is the tool written by Nissar Chababy AKA [@funilrys](https://github.com/funilrys) and used by the
[Ultimate Hosts Blacklist](https://github.com/ultimate-hosts-blacklist/ultimate.hosts.blacklist)
project to check the availability or syntax of a domain, IP or URL.
It delivers its status based on the result from WHOIS, DNS LOOKUP or even the
HTTP status code.

Please find more information about it there:

- http://pyfunceble.github.io
- http://pyfunceble.readthedocs.io
- https://github.com/funilrys/PyFunceble

