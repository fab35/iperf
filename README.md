iperf3:  A TCP, UDP, and SCTP network bandwidth measurement tool
================================================================

Summary
-------

iperf is a tool for active measurements of the maximum achievable
bandwidth on IP networks.  It supports tuning of various parameters
related to timing, protocols, and buffers.  For each test it reports
the measured throughput / bitrate, loss, and other parameters.

This version, sometimes referred to as iperf3, is a redesign of an
original version developed at NLANR/DAST.  iperf3 is a new
implementation from scratch, with the goal of a smaller, simpler code
base, and a library version of the functionality that can be used in
other programs. iperf3 also has a number of features found in other tools
such as nuttcp and netperf, but were missing from the original iperf.
These include, for example, a zero-copy mode and optional JSON output.
Note that iperf3 is *not* backwards compatible with the original iperf.

Primary development for iperf3 takes place on CentOS Linux, FreeBSD,
and macOS.  At this time, these are the only officially supported
platforms, however there have been some reports of success with
OpenBSD, NetBSD, Android, Solaris, and other Linux distributions.

iperf3 is principally developed by ESnet / Lawrence Berkeley National
Laboratory.  It is released under a three-clause BSD license.

For more information see: https://software.es.net/iperf

Source code and issue tracker: https://github.com/esnet/iperf

Obtaining iperf3
----------------

Downloads of iperf3 are available at:

    https://downloads.es.net/pub/iperf/

To check out the most recent code, clone the git repository at:

    https://github.com/esnet/iperf.git

Building iperf3
---------------

### Prerequisites: ###

None.

### Building ###

    ./configure; make; make install

(Note: If configure fails, try running `./bootstrap.sh` first)

Invoking iperf3
---------------

iperf3 includes a manual page listing all of the command-line options.
The manual page is the most up-to-date reference to the various flags and parameters.

For sample command line usage, see: 

https://fasterdata.es.net/performance-testing/network-troubleshooting-tools/iperf/

Using the default options, iperf is meant to show typical well
designed application performance.  "Typical well designed application"
means avoiding artificial enhancements that work only for testing
(such as splice()'ing the data to /dev/null).  iperf does also have
flags for "extreme best case" optimizations, but they must be
explicitly activated.

These flags include:

    -Z, --zerocopy            use a 'zero copy' sendfile() method of sending data
    -A, --affinity n/n,m      set CPU affinity

Bug Reports
-----------

Before submitting a bug report, please make sure you're running the
latest version of the code, and confirm that your issue has not
already been fixed.  Then submit to the iperf3 issue tracker on
GitHub:

https://github.com/esnet/iperf/issues

In your issue submission, please indicate the version of iperf3 and
what platform you're trying to run on (provide the platform
information even if you're not using a supported platform, we
*might* be able to help anyway).  Exact command-line arguments will
help us recreate your problem.  If you're getting error messages,
please include them verbatim if possible, but remember to sanitize any
sensitive information.

If you have a question about usage or about the code, please do *not*
submit an issue.  Please use one of the mailing lists for that.

Changes from iperf 2.x
----------------------

(Note that iperf2 is no longer being developed by its original
maintainers.  However, beginning in 2014, another developer began
fixing bugs and enhancing functionality, and generating releases of
iperf2.  Both projects (as of late 2017) are currently being developed
actively, but independently.  The continuing iperf2 development
project can be found at https://sourceforge.net/projects/iperf2/.)

New options:

    -V, --verbose             more detailed output than before
    -J, --json                output in JSON format
    -Z, --zerocopy            use a 'zero copy' sendfile() method of sending data
    -O, --omit N              omit the first n seconds (to ignore slowstart)
    -T, --title str           prefix every output line with this string
    -F, --file name           xmit/recv the specified file
    -A, --affinity n/n,m      set CPU affinity (Linux and FreeBSD only)
    -k, --blockcount #[KMG]   number of blocks (packets) to transmit (instead 
                              of -t or -n)
    -L, --flowlabel           set IPv6 flow label (Linux only)

Changed flags:

    -C, --linux-congestion    set congestion control algorithm (Linux only)
                              (-Z in iperf2)


Deprecated options:

Not planning to support these iperf2 flags. If you really miss these
options, please submit a request in the issue tracker:

    -d, --dualtest           Do a bidirectional test simultaneously
    -r, --tradeoff           Do a bidirectional test individually
    -T, --ttl                time-to-live, for multicast (default 1)
    -x, --reportexclude [CDMSV]   exclude C(connection) D(data) M(multicast) 
                                  S(settings) V(server) reports
    -y, --reportstyle C      report as a Comma-Separated Values

Also deprecated is the ability to set the options via environment
variables.

Known Issues
------------

A set of known issues is maintained on the iperf3 Web pages:

https://software.es.net/iperf/dev.html#known-issues

Links
-----

This section lists links to user-contributed Web pages regarding
iperf3.  ESnet and Lawrence Berkeley National Laboratory bear no
responsibility for the content of these pages.

* Installation instructions for Debian Linux (by Cameron Camp
  <cameron@ivdatacenter.com>):

  http://cheatsheet.logicalwebhost.com/iperf-network-testing/

Copyright
---------

iperf, Copyright (c) 2014-2018, The Regents of the University of
California, through Lawrence Berkeley National Laboratory (subject
to receipt of any required approvals from the U.S. Dept. of
Energy).  All rights reserved.

If you have questions about your rights to use or distribute this
software, please contact Berkeley Lab's Technology Transfer
Department at TTD@lbl.gov.

NOTICE.  This software is owned by the U.S. Department of Energy.
As such, the U.S. Government has been granted for itself and others
acting on its behalf a paid-up, nonexclusive, irrevocable,
worldwide license in the Software to reproduce, prepare derivative
works, and perform publicly and display publicly.  Beginning five
(5) years after the date permission to assert copyright is obtained
from the U.S. Department of Energy, and subject to any subsequent
five (5) year renewals, the U.S. Government is granted for itself
and others acting on its behalf a paid-up, nonexclusive,
irrevocable, worldwide license in the Software to reproduce,
prepare derivative works, distribute copies to the public, perform
publicly and display publicly, and to permit others to do so.

This code is distributed under a BSD style license, see the LICENSE
file for complete information.


SL/FP Observations and issues
-----------------------------
### CONFIG ###	

	PC iPerf	v.2.0.5 (08 Jul 2010) pthreads			v3.1.3 x64 (2016-04-21)	
    
	Rpi iPerf	v.2.0.5 (08 Jul 2010) pthreads			v3.0.7 (2019-01-22 compiled for armv7l Linux)			

### TESTS ###

See iperf_tests.xlsx for more details

	2019-02-20	(B2) IN THE LAB; WIRED; no RF TENT; @2452MHz; Adaura Att=[5,20,20,5] ie. 10dB att, RSSI=-35dBm (UDP60M; chn9)							Adaura Eth connected; AP moved					RSSI Signal level = -39dBm (iwconfig RPi)																						
	ID	TEST	IPERF version	TCP/UDP	Direction	Option Reverse	Config PC	Config Rpi	DispPC Tput (Mb/s)	DispRPi Tput (Mb/s)	PER (%)	Jitter (ms)		


	1	T2PRN_01	iperf2	TCP	Tx=Pc;Rx=Rpi + TCPack		iperf -c 192.168.1.100 -i1 -t20	iperf -s -i1 -t20																												

	2	T2PRN_01	iperf2	TCP	Tx=Pc;Rx=Rpi + TCPack																															

	3	T2RPN_01	iperf2	TCP	Tx=Rpi;Rx=Pc + TCPack		iperf -s -i1 -t20	iperf -c 192.168.1.160 -i1 -t20																												

	4	T2RPN_01	iperf2	TCP	Tx=Rpi;Rx=Pc + TCPack																															

	5	U2PRN_50_01	iperf2	UDP	Tx=Pc;Rx=Rpi		iperf -c 192.168.1.100 -u -b60M -i10 -t20 -V -fm	iperf -s -u -i10 -V -fm	51	52	13	0.35		<== iPERF2 SEEMS NEEDED TO HAVE GOOD OUTPUTS IN THIS UDP CONFIG from PC to RPi !?																						

	6	U2PRN_50_01	iperf2	UDP	Tx=Pc;Rx=Rpi										but iPerf2 seems unstable on the Rpi as an iperf server!																					

	7	U2RPN_50_01	iperf2	UDP	Tx=Rpi;Rx=Pc		iperf -s -u -i1 -t20	iperf -c 192.168.1.160 -u -b60M -i1 -t20																												

	8	U2RPN_50_01	iperf2	UDP	Tx=Rpi;Rx=Pc																															

	11	T3PRN_01	iperf3	TCP	Tx=Pc;Rx=Rpi + TCPack		iperf3 -c 192.168.1.100 -i10 -t20 -V -T[IPTA] -fm	iperf3 -s -i10 -V -fm	39.2 send / 39.2 rec	38.7 send / 38.7 rec				<== SEEMS RELIABLE for TCP from PC to Rpi (but can prefer -J option for JSON output)																						

	12	T3PRN_01	iperf3	TCP	Tx=Pc;Rx=Rpi + TCPack										use "iperf3 -c XX -V -iN -tN -J"  and "iperf3 -s -V -J"																					

	13	T3RPN_01	iperf3	TCP	Tx=Rpi;Rx=Pc + TCPack		iperf3 -s -i10 -V -fm	iperf3 -c 192.168.1.160 -i10 -t20 -V -T[IPTA] -fm	0 send / 29.3 rec	29.6 send / 29.4 rec				<== SEEMS RELIABLE for TCP from Rpi to PC iif looking at Rpi side only (but can prefer -J option for JSON output)																						
	14	T3RPN_01	iperf3	TCP	Tx=Rpi;Rx=Pc + TCPack										Issue for send value on the PC server side  (does not recover the value from Rpi?)																					
	11	T3PRN_01	iperf3	TCP	Tx=Pc;Rx=Rpi + TCPack	Reverse	iperf3 -s -i10 -V -fm	iperf3 -c 192.168.1.160 -i10 -t20 -R -V -T[IPTA] -fm	38.5 send / 0 rec	38.7 send / 38.7 rec																										
	12	T3PRN_01	iperf3	TCP	Tx=Pc;Rx=Rpi + TCPack	Reverse									Issue for received value on the PC server side  (does not recover the value from Rpi?)																					
	13	T3RPN_01	iperf3	TCP	Tx=Rpi;Rx=Pc + TCPack	Reverse	iperf3 -c 192.168.1.100 -i10 -t20 -R -V -T[IPTA] -fm	iperf3 -s -i10 -V -fm	30.3 send / 30.0 rec	29.8 send / 29.5 rec				<== SEEMS RELIABLE for TCP from Rpi to PC (but can prefer -J option for JSON output)																						

	14	T3RPN_01	iperf3	TCP	Tx=Rpi;Rx=Pc + TCPack	Reverse																														

	15	U3PRN_50_01	iperf3	UDP	Tx=Pc;Rx=Rpi		iperf3 -c 192.168.1.100 -u -b60M -i10 -t20 -V -T[IPTA] -fm	iperf3 -s -i10 -V -fm	59.8	58.8 (54 each 10s)	9.2	2.91		<== NOT RELIABLE FOR SUMMARY!  Summary report issues… Must remove lost packets if we look at status?																						

	16	U3PRN_50_01	iperf3	UDP	Tx=Pc;Rx=Rpi										Avoid this config iPerf, often buggy (note that values each s is also wrong after the first X seconds, when -iX is precised at PC client with max 10s)																					

	17	U3RPN_50_01	iperf3	UDP	Tx=Rpi;Rx=Pc		iperf3 -s -i10 -V -fm	iperf -c 192.168.1.160 -u -b60M -i10 -t20 -V -T[IPTA] -fm	0	34.8	0.01	0.63		<== SEEMS RELIABLE for UDP from Rpi to PC iif looking at Rpi side only (but can prefer -J option for JSON output)																						

	18	U3RPN_50_01	iperf3	UDP	Tx=Rpi;Rx=Pc										Issue for received value on the PC server side  (does not recover the value from Rpi?)																					

	19	U3RPR_50_01	iperf3	UDP	Tx=Pc;Rx=Rpi	Reverse	iperf3 -s -i10 -V -fm	iperf3 -c 192.168.1.160 -u -b60M -i10 -t20 -R -V -T[IPTA] -fm	59.9, Jitter 0	60.1 (54 each 10s)	9.3	1.13		<== NOT RELIABLE FOR SUMMARY!  Summary report issues… Must remove lost packets if we look at status?																						

	20	U3RPR_50_01	iperf3	UDP	Tx=Pc;Rx=Rpi	Reverse									Avoid this config iPerf, often buggy (note that values each s is also wrong after the first X seconds, when -iX is precised at PC client with max 10s)																					

	21	U3PRR_50_01	iperf3	UDP	Tx=Rpi;Rx=Pc	Reverse	iperf3 -c 192.168.1.100 -u -b60M -R -i10 -t20 -V -T[IPTA] -fm	iperf3 -s -i10 -V -fm	35.6	35.2	0.14	0.64		<== SEEMS RELIABLE for UDP from Rpi to PC (but can prefer -J option for JSON output)																						

	22	U3PRR_50_01	iperf3	UDP	Tx=Rpi;Rx=Pc	Reverse																							

### ISSUES ###

[iperf2]

	iperf2 does not behave the same on Linux/Rpi and Win/PC	
	
		* iperf2 PC->Rpi in UDP: the PC displays the TX packets (not the right correctly received) but the server report at the end is correct; except we observe a high PER (>5%) in our tests											
		
		* iperf2 Rpi->PC in UDP: the PC displays the same correct throughput on both sides (correctly received)+ server report at the end is correct; Note that PER is good (<0.1%) in our tests, but high Jitter variation (0.5 to 2ms)											
													
													
[iperf3]	

	iperf3 does not behave the same on the Win/PC (issues on sender report if PC server)	
	
		* iperf3 displays the proper values (sender/receiver) in TCP on the client; but not the proper Rpi (sender on non-reversed mode) throughput on the PC-server when the PC is the server (0 displayed). Same issue in UDP (PC-server displays 0)											
		
		* iPerf3 issues: summary results UDP BW from PC to Rpi.    PC-client to RPi-server; only BW at each second on RPi-server side is OK.   Summary seems overestimated (full-rate, differs from average value)											
		
		* This is also true in REVERSE mode: RPi-client to PC-server; only BW at each second on RPi-client side is OK.  Note that Jitter at PC-server side is also wrong (0)											
		
		* Perhaps bugs have been resolved in newer versions of iPerf; but how to find a recent version for Raspbian ? (someome to recompile it?)											

