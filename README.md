# nagios-plugin-check_zone_serial

Nagios plugin to monitor zone file serials across nameservers.

This can be run on any host via NRPE, but is best off being run on the Nagios
host.

## Dependencies

* Getopt::Long Perl module
* Nagios::Plugin Perl Module
* Net::DNS::Resolver Perl Module

## Installation

* Copy the `check_zone_serial` to your nagios plugin folder and set executable.

* If running via NRPE add a line to your `nrpe.cfg` file
```
command[check_zone_serial]=/usr/lib/nagios/plugins/check_zone_serial -d example.com
```

* If running via Nagios add a line to your nagios config file
```
define command{
    command_name    check_zone_serial
    command_line    /tmp/check_zone_serial -d example.com
}
define service{
        use                             generic-service         ; Name of service template to use
        host_name                       localhost
        service_description             ZONESYNC
        check_command                   check_zone_serial
        }
```

## Examples

* Run with the --help argument to see all options
```
check_zone_serial --help
```

* Check domains against the nameservers listed under NS records
```
check_zone_serial -d example.com -d example.org
```

* Check domains against specific nameservers
```
check_zone_serial -d example.com -n ns1.example.net ns2.example.net
```

* Check domain names listed in a text file
```
check_zone_serial -f /path/to/domains.txt
```
## Future Work

None planned

## Site

https://github.com/alasdairkeyes/nagios-plugin-check_zone_serial

## Author

* Alasdair Keyes - https://akeyes.co.uk/

## License

Released under GPL V3 - See included license file.
