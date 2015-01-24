check_http_xml
==========

Nagios plugin to check XML attributes via http(s).

This Plugin is a fork of the existing JSON Plugin from https://github.com/c-kr/check_json https://github.com/bbuchalter/check_json with the enhancements of using the Nagios::Plugin Perl Module, allowing to use thresholds and performance data collection from various json attributes.

Performance data is also enhanced to extract performance data compliant to Nagios and Graphite standards. One attribute is selected for thresholds check, multiple others can be added for extracting performance data. This plugin is aimed at simplifying Nagios, Icinga & Icinga2 polling of XML status APIs.

Usage: 
```
check_http_xml -u|--url <URL> -a|--attribute <attribute> [ -c|--critical <threshold> ] [ -w|--warning <threshold> ] [ -p|--perfvars <fields> ] [ -o|--outputvars <fields> ] [ -t|--timeout <timeout> ] [ -d|--divisor <divisor> ] [ -T|--contenttype <content-type> ] [ --ignoressl ] [ -h|--help ]
```

Example: 
```
./check_http_xml.pl --url http://192.168.5.10:9332/local_stats --attribute '{shares}->{dead_shares}' --warning :5 --critical :10 --perfvars '{shares}->{dead_shares},{shares}->{live_shares},{clients}->{clients_connected}'
```

Result:
```
Check XML status API OK - dead_shares: 2, live_shares: 12, clients_connected: 234 | dead_shares=2;5;10 live_shares=12 clients_connected=234
```

Requirements
============

Perl XML package

* Debian : libxml-simple-perl
* Redhat : perl-XML-Simple.noarch

