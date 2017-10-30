Forager  ![alt tag](img/Forager.png)
=======

[![Build Status](https://travis-ci.org/byt3smith/Forager.svg?branch=master)](https://travis-ci.org/byt3smith/Forager)

##### Summary

  Do you ever wonder if there is an easier way to retrieve, store, and maintain all your threat intelligence data? Random user, meet Forager. Not all threat intel implementations require a database that is "correlating trillions of data points.." and instead, you just need a simple interface, with simple TXT files, that can pull threat data from other feeds, PDF threat reports, or other data sources, with minimal effort. With 15 pre-configured threat feeds, you can get started with threat intelligence feed management today.. Right now.. Do it!

##### Features At A Glance

* Fetch intel from URL's using modular feed functions
* Extract domain, md5, sha1, sha256, IPv4, and YARA indicators
* Search through the current intel set by single IP or with an IOC file
* Generate JSON feeds for consumption by CarbonBlack
* Serves up a Simple HTTP JSON feed server for CarbonBlack

Requirements:
-------
*Requires Python 3!*
* argparse
* xlrd
* pdfminer3k
* colorama (for pretty colored output)

You can install all requirements with the included requirements.txt file
```
pip3 install -r requirements.txt
```

Feeds `--feeds`
--------
* `list` -- Lists all feeds and allows user to choose a single feed to update.
* `update` -- Updates all feed modules listed in Forager

Hunting `--hunt`
---------
* `-f [file path]` Provides the capability to search through the intel directory results for a specific list of indicators
* `-s [IPv4 address]` Searches through intel directory for a single IP address

Extraction `--extract`
----------
* Reads in a file and extracts IP addresss, domains, MD5/SHA1/SHA256 hashes, and YARA rules
* Places the extracted indicators into the intel directory
* Currently supported filetypes:
  * TXT
  * PDF
  * XLS/XLSX

Note:

* Prone to false positives when extracting indicators from PDF as whitepapers with indicators will normally also contain URL references

CarbonBlack Feed Generator `--cbgen`
-----------------
* Generates JSON feeds of all of the IOCs in the intel dir
* Utilizes an interactive CLI prompt to allow the user to provide feed metadata the first time CBgen is run

CarbonBlack Feed Server `--srv`
----------------
* Runs the built-in feed server so that the CarbonBlack server can automatically ingest the JSON feeds that were generated by the CBgen command
