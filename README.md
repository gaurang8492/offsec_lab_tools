Tools for Offsec PWB Labs
========

axfr.rb
--------

An example Ruby script that attempts a full DNS zone transfer (AXFR) using dnsruby

```
Usage: axfr.rb [options] zone

Available options:
    -n, --nameserver HOSTNAME        Specify the nameserver to AXFR zone from
    -w, --timeout SECONDS            Wait timeout in seconds
    -v, --verbose                    Be more verbose
    -h, --help                       Show this help
```

smtpvrfy.rb
--------

Multithreaded SMTP user enumartion tool. You can fine tune the number of threads and users checked in one connection. 
Please note that some SMTP servers might not allow you to do more than a few VRFY calls. The default is to 
reconnect after checkign 3 users. Without the dictionary file the tool only checks for a few standard users. 

```
# ./smtpvrfy.rb -h
Usage: smtpvrfy.rb [options] SMTP_SERVER[:PORT]
Where available options:
    -t, --threads N                  Number of threads (connections) to use - Default: 50
    -c, --chunk N                    Recycle the connection (thread) after N number of users checked - Default: 3
    -u, --user FILE                  Read a dict file with users
    -d, --debug                      Enable session debug
    -h, --help                       Show this help

``` 
Example:

```
# ./smtpvrfy.rb -t 10 -c 5 -u userdict.txt 192.168.11.215
Time: 00:00:20 |===================================================>>| 100% VRFY
adm@redhat.acme.com
apache@redhat.acme.com
bin@redhat.acme.com
bob@redhat.acme.com
```
mping.sh
---------

Just a simple Bash script that indentifies all live hosts (responding to ping) on a given network(s).

```
Usage: ./mping.sh [-t] <IP Range>[,<IP Range>]
  Options:
  -t <n>: Number of ping threads to use (Default: 50)
  -v    : Verbose mode

  Example:
      ./mping.sh 192.168.11.200-192.168.11.254
      ./mping.sh -t 100 192.168.1.1-192.168.1.100,10.1.0.0-10.2.1.1

```

mping.rb
--------
Just a simple Ruby script that indentifies all live hosts (responding to ping) on a given network(s).

```
# ./mping.rb 
Usage:
    mping.rb [options]
    -t, --thread [N]                 Threads to spawn
    -v, --verbose                    Run verbosely
    -h, --help                       Show help
Example:
    mping.rb 192.168.10.200-192.168.10.254
    mping.rb -t 100 10.1.2.3-10.1.2.254,192.168.1.1-192.168.10.254
```
Example:

```
# ./mping.rb -t100 192.168.11.200-192.168.11.254,192.168.13.200-192.168.13.254,192.168.15.200-192.168.15.254,192.168.17.200-192.168.17.254 
Time: 00:00:10 |===============================================================================================================================================================================>>| 100% Ping
192.168.11.201
192.168.11.202
192.168.11.205
192.168.11.206
192.168.11.208
```
