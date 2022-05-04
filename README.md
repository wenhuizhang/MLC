# Memory Latency Checker


The goal is to test memory latency difference w/ and w/o SMT.


You can check the state of SMT with
```
cat /sys/devices/system/cpu/smt/active
```

And change the state with:

```
echo off > /sys/devices/system/cpu/smt/control

```


With SMT:
```
./mlc
Intel(R) Memory Latency Checker - v3.9a
Measuring idle latencies (in ns)...
		Numa node
Numa node	     0	     1	
       0	  78.5	 134.8	
       1	 133.7	  79.2	

Measuring Peak Injection Memory Bandwidths for the system
Bandwidths are in MB/sec (1 MB/sec = 1,000,000 Bytes/sec)
Using all the threads from each core if Hyper-threading is enabled
Using traffic with the following read-write ratios
ALL Reads        :	222557.1	
3:1 Reads-Writes :	207303.4	
2:1 Reads-Writes :	205252.9	
1:1 Reads-Writes :	197367.3	
Stream-triad like:	184524.3	

Measuring Memory Bandwidths between nodes within system 
Bandwidths are in MB/sec (1 MB/sec = 1,000,000 Bytes/sec)
Using all the threads from each core if Hyper-threading is enabled
Using Read-only traffic type
		Numa node
Numa node	     0	     1	
       0	111388.0	51085.7	
       1	51081.0	111529.8	

Measuring Loaded Latencies for the system
Using all the threads from each core if Hyper-threading is enabled
Using Read-only traffic type
Inject	Latency	Bandwidth
Delay	(ns)	MB/sec
==========================
 00000	252.82	 222894.0
 00002	253.50	 222858.7
 00008	252.77	 222957.4
 00015	253.50	 223114.1
 00050	251.09	 223272.7
 00100	244.21	 222969.8
 00200	125.49	 188404.7
 00300	101.84	 131250.4
 00400	 97.61	 100028.0
 00500	 95.99	  80892.6
 00700	 94.60	  58536.7
 01000	 91.29	  41548.5
 01300	 86.04	  32326.8
 01700	 84.35	  24986.2
 02500	 82.65	  17299.8
 03500	 82.38	  12600.9
 05000	 81.76	   9074.8
 09000	 81.45	   5396.7
 20000	 79.83	   2878.4

Measuring cache-to-cache transfer latency (in ns)...
Local Socket L2->L2 HIT  latency	50.3
Local Socket L2->L2 HITM latency	50.3
Remote Socket L2->L2 HITM latency (data address homed in writer socket)
			Reader Numa Node
Writer Numa Node     0	     1	
            0	     -	 112.8	
            1	 112.7	     -	
Remote Socket L2->L2 HITM latency (data address homed in reader socket)
			Reader Numa Node
Writer Numa Node     0	     1	
            0	     -	 176.5	
            1	 177.3	     -	
```

Without MLC
```
 ./mlc 
Intel(R) Memory Latency Checker - v3.9a
Measuring idle latencies (in ns)...
		Numa node
Numa node	     0	     1	
       0	  78.5	 134.8	
       1	 133.7	  79.2	

Measuring Peak Injection Memory Bandwidths for the system
Bandwidths are in MB/sec (1 MB/sec = 1,000,000 Bytes/sec)
Using all the threads from each core if Hyper-threading is enabled
Using traffic with the following read-write ratios
ALL Reads        :	226326.3	
3:1 Reads-Writes :	209234.5	
2:1 Reads-Writes :	207599.9	
1:1 Reads-Writes :	197546.5	
Stream-triad like:	191025.0	

Measuring Memory Bandwidths between nodes within system 
Bandwidths are in MB/sec (1 MB/sec = 1,000,000 Bytes/sec)
Using all the threads from each core if Hyper-threading is enabled
Using Read-only traffic type
		Numa node
Numa node	     0	     1	
       0	113227.2	51342.8	
       1	51358.3	113237.1	

Measuring Loaded Latencies for the system
Using all the threads from each core if Hyper-threading is enabled
Using Read-only traffic type
Inject	Latency	Bandwidth
Delay	(ns)	MB/sec
==========================
 00000	266.00	 226520.0
 00002	263.08	 226417.0
 00008	262.86	 226524.5
 00015	264.75	 227171.4
 00050	238.83	 230500.5
 00100	178.15	 226078.4
 00200	118.28	 169321.7
 00300	106.08	 124954.8
 00400	102.56	  97018.4
 00500	 99.12	  78967.9
 00700	 92.49	  57617.3
 01000	 89.20	  41099.2
 01300	 88.05	  32030.6
 01700	 85.31	  24785.1
 02500	 84.55	  17195.3
 03500	 84.22	  12542.8
 05000	 84.63	   9017.4
 09000	 83.73	   5354.9
 20000	 82.04	   2852.6

Measuring cache-to-cache transfer latency (in ns)...
Local Socket L2->L2 HIT  latency	50.3
Local Socket L2->L2 HITM latency	50.3
Remote Socket L2->L2 HITM latency (data address homed in writer socket)
			Reader Numa Node
Writer Numa Node     0	     1	
            0	     -	 112.7	
            1	 112.7	     -	
Remote Socket L2->L2 HITM latency (data address homed in reader socket)
			Reader Numa Node
Writer Numa Node     0	     1	
            0	     -	 177.2	
            1	 177.2	     -	
```
