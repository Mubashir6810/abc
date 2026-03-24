SE446 Project - Group 10
-
 Team Members
-
Alanoud Almeniya (231385)

Lina Dardeer (231709)

Masa Abara (231837)

Noura Altuwaijri (231222)

Executive Summary
-
In this project, we used Hadoop MapReduce to analyze a large crime dataset and gain meaningful insights. We implemented Python-based mappers and reducers to identify common crime types, high-risk locations, and trends over time. Our findings showed that theft is the most frequent crime, and streets and residential areas are the main hotspots. We also observed a significant increase in crime in recent years along with a low arrest rate. This project helped us understand how distributed data processing can be used to support real-world decision-making.

 Task 2: Crime Type Analysis
-
  Command 
-
```bash
mapred streaming \
  -files mapper_task2.py,reducer_sum.py \
  -mapper "python3 mapper_task2.py" \
  -reducer "python3 reducer_sum.py" \
  -input /data/chicago_crimes_sample.csv \
  -output /user/aalmeniya/task2_output
```
  Sample Output
-
```
ARSON    21
ASSAULT  878
BATTERY  1728
BURGLARY 316
CONCEALED CARRY LICENSE VIOLATION 6
```
  Interpretation
-
Theft is the most common crime (~20.5%), followed by Battery (17.3%) and Criminal Damage (10.6%).

  Execution Logs
-
```
Last login: Sun Feb 22 19:37:32 on ttys000
alanoud@ALANOUDs-MBP ~ % cd /Users/alanoud/Downloads/Project/chicago_project/src
alanoud@ALANOUDs-MBP src % scp mapper_task2.py reducer_sum.py aalmeniya@134.209.172.50:~/
aalmeniya@134.209.172.50's password:
mapper_task2.py                               100%  196     1.0KB/s   00:00  
reducer_sum.py                                100%  489     2.5KB/s   00:00  
alanoud@ALANOUDs-MBP src % ssh aalmeniya@134.209.172.50
aalmeniya@134.209.172.50's password:
Welcome to Ubuntu 22.04.5 LTS (GNU/Linux 5.15.0-170-generic x86_64)
Documentation:  https://help.ubuntu.com
Management:     https://landscape.canonical.com
Support:        https://ubuntu.com/pro
System information as of Sun Feb 22 16:58:14 UTC 2026
System load:  0.06               Processes:             122
Usage of /:   19.8% of 77.35GB   Users logged in:       1
Memory usage: 43%                IPv4 address for eth0: 134.209.172.50
Swap usage:   0%                 IPv4 address for eth0: 10.17.0.5
Expanded Security Maintenance for Applications is not enabled.
6 updates can be applied immediately.
To see these additional updates run: apt list --upgradable
Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status
New release '24.04.4 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Sun Feb 22 16:52:46 2026 from 134.209.172.50
aalmeniya@master-node:~$ source /etc/profile.d/hadoop.sh
aalmeniya@master-node:~$ ls
bigfile.dat  downloaded_test.txt  mapper_task2.py  reducer_sum.py  test.txt
aalmeniya@master-node:~$ mapred streaming  
-files mapper_task2.py,reducer_sum.py  
-mapper "python3 mapper_task2.py"  
-reducer "python3 reducer_sum.py"  
-input /data/chicago_crimes_sample.csv  
-output /user/aalmeniya/task2_output
packageJobJar: [] [/opt/hadoop-3.4.1/share/hadoop/tools/lib/hadoop-streaming-3.4.1.jar] /tmp/streamjob9382272243764188553.jar tmpDir=null
2026-02-22 17:00:54,634 INFO client.DefaultNoHARMFailoverProxyProvider: Connecting to ResourceManager at master-node/134.209.172.50:8032
2026-02-22 17:00:54,931 INFO client.DefaultNoHARMFailoverProxyProvider: Connecting to ResourceManager at master-node/134.209.172.50:8032
2026-02-22 17:00:55,319 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /tmp/hadoop-yarn/staging/aalmeniya/.staging/job_1771402826595_0047
2026-02-22 17:00:56,950 INFO mapred.FileInputFormat: Total input files to process : 1
2026-02-22 17:00:58,079 INFO mapreduce.JobSubmitter: number of splits:2
2026-02-22 17:00:58,936 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1771402826595_0047
2026-02-22 17:00:58,937 INFO mapreduce.JobSubmitter: Executing with tokens: []
2026-02-22 17:00:59,250 INFO conf.Configuration: resource-types.xml not found
2026-02-22 17:00:59,251 INFO resource.ResourceUtils: Unable to find 'resource-types.xml'.
2026-02-22 17:00:59,369 INFO impl.YarnClientImpl: Submitted application application_1771402826595_0047
2026-02-22 17:00:59,421 INFO mapreduce.Job: The url to track the job: http://master-node:8088/proxy/application_1771402826595_0047/
2026-02-22 17:00:59,424 INFO mapreduce.Job: Running job: job_1771402826595_0047
2026-02-22 17:01:19,147 INFO mapreduce.Job: Job job_1771402826595_0047 running in uber mode : false
2026-02-22 17:01:19,149 INFO mapreduce.Job:  map 0% reduce 0%
2026-02-22 17:01:38,426 INFO mapreduce.Job:  map 100% reduce 0%
2026-02-22 17:01:52,669 INFO mapreduce.Job:  map 100% reduce 100%
2026-02-22 17:01:55,420 INFO mapreduce.Job: Job job_1771402826595_0047 completed successfully
2026-02-22 17:01:55,658 INFO mapreduce.Job: Counters: 54
File System Counters
FILE: Number of bytes read=159339
FILE: Number of bytes written=1261856
FILE: Number of read operations=0
FILE: Number of large read operations=0
FILE: Number of write operations=0
HDFS: Number of bytes read=2391502
HDFS: Number of bytes written=541
HDFS: Number of read operations=11
HDFS: Number of large read operations=0
HDFS: Number of write operations=2
HDFS: Number of bytes read erasure-coded=0
Job Counters
Launched map tasks=2
Launched reduce tasks=1
Data-local map tasks=2
Total time spent by all maps in occupied slots (ms)=66130
Total time spent by all reduces in occupied slots (ms)=20998
Total time spent by all map tasks (ms)=33065
Total time spent by all reduce tasks (ms)=10499
Total vcore-milliseconds taken by all map tasks=33065
Total vcore-milliseconds taken by all reduce tasks=10499
Total megabyte-milliseconds taken by all map tasks=16929280
Total megabyte-milliseconds taken by all reduce tasks=5375488
Map-Reduce Framework
Map input records=10001
Map output records=10000
Map output bytes=139333
Map output materialized bytes=159345
Input split bytes=212
Combine input records=0
Combine output records=0
Reduce input groups=29
Reduce shuffle bytes=159345
Reduce input records=10000
Reduce output records=29
Spilled Records=20000
Shuffled Maps =2
Failed Shuffles=0
Merged Map outputs=2
GC time elapsed (ms)=936
CPU time spent (ms)=3440
Physical memory (bytes) snapshot=666161152
Virtual memory (bytes) snapshot=6560636928
Total committed heap usage (bytes)=348164096
Peak Map Physical memory (bytes)=264712192
Peak Map Virtual memory (bytes)=2184790016
Peak Reduce Physical memory (bytes)=148721664
Peak Reduce Virtual memory (bytes)=2191060992
Shuffle Errors
BAD_ID=0
CONNECTION=0
IO_ERROR=0
WRONG_LENGTH=0
WRONG_MAP=0
WRONG_REDUCE=0
File Input Format Counters
Bytes Read=2391290
File Output Format Counters
Bytes Written=541
2026-02-22 17:01:55,659 INFO streaming.StreamJob: Output directory: /user/aalmeniya/task2_output
aalmeniya@master-node:~$ hdfs dfs -cat /user/aalmeniya/task2_output/part-00000
ARSON	21
ASSAULT	878
BATTERY	1728
BURGLARY	316
CONCEALED CARRY LICENSE VIOLATION	6
CRIM SEXUAL ASSAULT	4
CRIMINAL DAMAGE	1062
CRIMINAL SEXUAL ASSAULT	107
CRIMINAL TRESPASS	153
DECEPTIVE PRACTICE	799
GAMBLING	1
HOMICIDE	44
HUMAN TRAFFICKING	2
INTERFERENCE WITH PUBLIC OFFICER	26
INTIMIDATION	5
KIDNAPPING	5
LIQUOR LAW VIOLATION	6
MOTOR VEHICLE THEFT	948
NARCOTICS	159
OBSCENITY	1
OFFENSE INVOLVING CHILDREN	137
OTHER OFFENSE	586
PROSTITUTION	6
PUBLIC PEACE VIOLATION	34
ROBBERY	508
SEX OFFENSE	96
STALKING	24
THEFT	2054
WEAPONS VIOLATION	284
```
 Task 3: Location Hotspots
-
  Command
-
```bash
mapred streaming \
  -files mapper_task3.py,reducer_sum.py \
  -mapper "python3 mapper_task3.py" \
  -reducer "python3 reducer_sum.py" \
  -input /data/chicago_crimes_sample.csv \
  -output /user/mabara/task3_output
```
  Sample Output
-
```
STREET     2737
APARTMENT  1909
RESIDENCE  1358
SIDEWALK   536
PARKING LOT / GARAGE  362
```
  Interpretation
-
Most crimes occur on Street, followed by Apartment and Residence, indicating that public areas and residential zones are the main crime hotspots.

  Execution Logs
-
```
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.
Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows
PS C:\Users\HUAWEI> cd C:\Users\HUAWEI\Downloads\chicago_project\src
PS C:\Users\HUAWEI\Downloads\chicago_project\src> scp mapper_task3.py reducer_sum.py mabara@134.209.172.50:~/
mabara@134.209.172.50's password:
mapper_task3.py                                                                                                           100%  189     1.0KB/s   00:00
reducer_sum.py                                                                                                            100%  489     2.4KB/s   00:00
PS C:\Users\HUAWEI\Downloads\chicago_project\src> ssh mabara@134.209.172.50
mabara@134.209.172.50's password:
Welcome to Ubuntu 22.04.5 LTS (GNU/Linux 5.15.0-170-generic x86_64)
Documentation:  https://help.ubuntu.com
Management:     https://landscape.canonical.com
Support:        https://ubuntu.com/pro
System information as of Wed Mar 18 03:59:36 UTC 2026
System load:  0.01               Processes:             117
Usage of /:   21.6% of 77.35GB   Users logged in:       0
Memory usage: 50%                IPv4 address for eth0: 134.209.172.50
Swap usage:   0%                 IPv4 address for eth0: 10.17.0.5
Expanded Security Maintenance for Applications is not enabled.
11 updates can be applied immediately.
To see these additional updates run: apt list --upgradable
Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status

*** System restart required ***
mabara@master-node:~$ source /etc/profile.d/hadoop.sh
mabara@master-node:~$ mapred streaming  
-files mapper_task3.py,reducer_sum.py  
-mapper "python3 mapper_task3.py"  
-reducer "python3 reducer_sum.py"  
-input /data/chicago_crimes_sample.csv  
-output /user/mabara/task3_output
packageJobJar: [] [/opt/hadoop-3.4.1/share/hadoop/tools/lib/hadoop-streaming-3.4.1.jar] /tmp/streamjob14228216000636021704.jar tmpDir=null
2026-03-18 04:11:47,579 INFO client.DefaultNoHARMFailoverProxyProvider: Connecting to ResourceManager at master-node/134.209.172.50:8032
2026-03-18 04:11:47,957 INFO client.DefaultNoHARMFailoverProxyProvider: Connecting to ResourceManager at master-node/134.209.172.50:8032
2026-03-18 04:11:48,550 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /tmp/hadoop-yarn/staging/mabara/.staging/job_1771402826595_0094
2026-03-18 04:11:50,408 INFO mapred.FileInputFormat: Total input files to process : 1
2026-03-18 04:11:51,016 INFO mapreduce.JobSubmitter: number of splits:2
2026-03-18 04:11:51,804 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1771402826595_0094
2026-03-18 04:11:51,805 INFO mapreduce.JobSubmitter: Executing with tokens: []
2026-03-18 04:11:52,144 INFO conf.Configuration: resource-types.xml not found
2026-03-18 04:11:52,145 INFO resource.ResourceUtils: Unable to find 'resource-types.xml'.
2026-03-18 04:11:52,278 INFO impl.YarnClientImpl: Submitted application application_1771402826595_0094
2026-03-18 04:11:52,340 INFO mapreduce.Job: The url to track the job: http://master-node:8088/proxy/application_1771402826595_0094/
2026-03-18 04:11:52,343 INFO mapreduce.Job: Running job: job_1771402826595_0094
2026-03-18 04:12:09,052 INFO mapreduce.Job: Job job_1771402826595_0094 running in uber mode : false
2026-03-18 04:12:09,054 INFO mapreduce.Job:  map 0% reduce 0%
2026-03-18 04:12:25,792 INFO mapreduce.Job:  map 100% reduce 0%
2026-03-18 04:12:35,311 INFO mapreduce.Job:  map 100% reduce 100%
2026-03-18 04:12:38,066 INFO mapreduce.Job: Job job_1771402826595_0094 completed successfully
2026-03-18 04:12:38,290 INFO mapreduce.Job: Counters: 54
File System Counters
FILE: Number of bytes read=167407
FILE: Number of bytes written=1277878
FILE: Number of read operations=0
FILE: Number of large read operations=0
FILE: Number of write operations=0
HDFS: Number of bytes read=2391502
HDFS: Number of bytes written=2628
HDFS: Number of read operations=11
HDFS: Number of large read operations=0
HDFS: Number of write operations=2
HDFS: Number of bytes read erasure-coded=0
Job Counters
Launched map tasks=2
Launched reduce tasks=1
Data-local map tasks=2
Total time spent by all maps in occupied slots (ms)=55630
Total time spent by all reduces in occupied slots (ms)=13850
Total time spent by all map tasks (ms)=27815
Total time spent by all reduce tasks (ms)=6925
Total vcore-milliseconds taken by all map tasks=27815
Total vcore-milliseconds taken by all reduce tasks=6925
Total megabyte-milliseconds taken by all map tasks=14241280
Total megabyte-milliseconds taken by all reduce tasks=3545600
Map-Reduce Framework
Map input records=10001
Map output records=10000
Map output bytes=147401
Map output materialized bytes=167413
Input split bytes=212
Combine input records=0
Combine output records=0
Reduce input groups=111
Reduce shuffle bytes=167413
Reduce input records=10000
Reduce output records=110
Spilled Records=20000
Shuffled Maps =2
Failed Shuffles=0
Merged Map outputs=2
GC time elapsed (ms)=451
CPU time spent (ms)=2670
Physical memory (bytes) snapshot=644284416
Virtual memory (bytes) snapshot=6562820096
Total committed heap usage (bytes)=347766784
Peak Map Physical memory (bytes)=250974208
Peak Map Virtual memory (bytes)=2187407360
Peak Reduce Physical memory (bytes)=144658432
Peak Reduce Virtual memory (bytes)=2191630336
Shuffle Errors
BAD_ID=0
CONNECTION=0
IO_ERROR=0
WRONG_LENGTH=0
WRONG_MAP=0
WRONG_REDUCE=0
File Input Format Counters
Bytes Read=2391290
File Output Format Counters
Bytes Written=2628
2026-03-18 04:12:38,296 INFO streaming.StreamJob: Output directory: /user/mabara/task3_output
mabara@master-node:~$ hdfs dfs -cat /user/mabara/task3_output/part-00000
ABANDONED BUILDING      2
AIRCRAFT        1
AIRPORT BUILDING NON-TERMINAL - NON-SECURE AREA 2
AIRPORT EXTERIOR - NON-SECURE AREA      2
AIRPORT EXTERIOR - SECURE AREA  3
AIRPORT PARKING LOT     8
AIRPORT TERMINAL LOWER LEVEL - NON-SECURE AREA  5
AIRPORT TERMINAL LOWER LEVEL - SECURE AREA      5
AIRPORT TERMINAL UPPER LEVEL - NON-SECURE AREA  4
AIRPORT TERMINAL UPPER LEVEL - SECURE AREA      11
AIRPORT TRANSPORTATION SYSTEM (ATS)     1
AIRPORT VENDING ESTABLISHMENT   1
AIRPORT/AIRCRAFT        1
ALLEY   219
ANIMAL HOSPITAL 2
APARTMENT       1909
APPLIANCE STORE 5
ATHLETIC CLUB   14
ATM (AUTOMATIC TELLER MACHINE)  8
AUTO    2
AUTO / BOAT / RV DEALERSHIP     9
BANK    37
BAR OR TAVERN   84
BARBERSHOP      5
BOAT / WATERCRAFT       2
BRIDGE  2
CAR WASH        9
CEMETARY        2
CHA APARTMENT   15
CHA HALLWAY / STAIRWELL / ELEVATOR      7
CHA PARKING LOT / GROUNDS       17
CHURCH / SYNAGOGUE / PLACE OF WORSHIP   16
CLEANING STORE  1
COIN OPERATED MACHINE   1
COLLEGE / UNIVERSITY - GROUNDS  3
COLLEGE / UNIVERSITY - RESIDENCE HALL   2
COMMERCIAL / BUSINESS OFFICE    128
CONSTRUCTION SITE       11
CONVENIENCE STORE       51
CREDIT UNION    1
CTA BUS 48
CTA BUS STOP    16
CTA PARKING LOT / GARAGE / OTHER PROPERTY       6
CTA PLATFORM    25
CTA STATION     24
CTA TRACKS - RIGHT OF WAY       3
CTA TRAIN       51
CURRENCY EXCHANGE       6
DAY CARE CENTER 6
DEPARTMENT STORE        134
DRIVEWAY - RESIDENTIAL  25
DRUG STORE      46
FACTORY / MANUFACTURING BUILDING        3
FEDERAL BUILDING        1
GAS STATION     124
GAS STATION DRIVE/PROP. 1
GOVERNMENT BUILDING / PROPERTY  19
GROCERY FOOD STORE      92
HALLWAY 1
HIGHWAY / EXPRESSWAY    3
HOSPITAL BUILDING / GROUNDS     50
HOSPITAL BUILDING/GROUNDS       1
HOTEL / MOTEL   41
HOTEL/MOTEL     3
HOUSE   1
JAIL / LOCK-UP FACILITY 2
LAKEFRONT / WATERFRONT / RIVERBANK      4
LIBRARY 6
MEDICAL / DENTAL OFFICE 11
MOVIE HOUSE / THEATER   5
NURSING / RETIREMENT HOME       42
NURSING HOME/RETIREMENT HOME    1
OTHER   10
OTHER (SPECIFY) 156
OTHER COMMERCIAL TRANSPORTATION 6
OTHER RAILROAD PROPERTY / TRAIN DEPOT   3
PARK PROPERTY   92
PARKING LOT / GARAGE (NON RESIDENTIAL)  362
PARKING LOT/GARAGE(NON.RESID.)  1
PAWN SHOP       1
POLICE FACILITY / VEHICLE PARKING LOT   39
POLICE FACILITY/VEH PARKING LOT 1
PORCH   2
RESIDENCE       1358
RESIDENCE - GARAGE      118
RESIDENCE - PORCH / HALLWAY     101
RESIDENCE - YARD (FRONT / BACK) 130
RESIDENCE PORCH/HALLWAY 1
RESIDENCE-GARAGE        1
RESTAURANT      187
RETAIL STORE    1
SCHOOL - PRIVATE BUILDING       13
SCHOOL - PRIVATE GROUNDS        9
SCHOOL - PUBLIC BUILDING        87
SCHOOL - PUBLIC GROUNDS 76
SIDEWALK        536
SMALL RETAIL STORE      234
SPORTS ARENA / STADIUM  13
STREET  2737
TAVERN / LIQUOR STORE   17
TAXICAB 6
VACANT LOT      1
VACANT LOT / LAND       31
VACANT LOT/LAND 2
VEHICLE - COMMERCIAL    11
VEHICLE - DELIVERY TRUCK        1
VEHICLE - OTHER RIDE SHARE SERVICE (LYFT, UBER, ETC.)   5
VEHICLE NON-COMMERCIAL  139
VESTIBULE       1
WAREHOUSE       9
mabara@master-node:~$ hdfs dfs -cat /user/mabara/task3_output/part-00000 > task3_result.txt
mabara@master-node:~$ exit
logout
Connection to 134.209.172.50 closed.
PS C:\Users\HUAWEI\Downloads\chicago_project\src> scp mabara@134.209.172.50:~/task3_result.txt .
mabara@134.209.172.50's password:
task3_result.txt                                                                                                                        100% 2628    13.4KB/s   00:00
PS C:\Users\HUAWEI\Downloads\chicago_project\src>
```
 Task 4: Crime Trend Over Time
-
  Command
-
```bash
mapred streaming \
  -files mapper_task4.py,reducer_sum.py \
  -mapper "python3 mapper_task4.py" \
  -reducer "python3 reducer_sum.py" \
  -input /data/chicago_crimes_sample.csv \
  -output /user/naltuwajiri/task4_output
```
  Sample Output
-
```
2001 4
2005 19
2015 28
2021 83
2022 135
2023 9446
2024 39
```
  Interpretation
-
Crime rates remained relatively low for years, gradually increased, spiked dramatically in 2023, and then sharply declined in 2024.

  Execution Logs
-
```
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

Install the latest PowerShell for new features and improvements! https://aka.ms/PSWindows

PS C:\Users\Surface Pro> cd Downloads\chicago_project\chicago_project\src
PS C:\Users\Surface Pro\Downloads\chicago_project\chicago_project\src> scp mapper_task4.py reducer_sum.py naltuwajiri@134.209.172.50:~/
naltuwajiri@134.209.172.50's password:
mapper_task4.py                                                                       100%  336     1.6KB/s   00:00
reducer_sum.py                                                                        100%  489     2.3KB/s   00:00
PS C:\Users\Surface Pro\Downloads\chicago_project\chicago_project\src> ssh naltuwajiri@134.209.172.50
naltuwajiri@134.209.172.50's password:
Welcome to Ubuntu 22.04.5 LTS (GNU/Linux 5.15.0-170-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Wed Mar 18 03:59:36 UTC 2026

  System load:  0.01               Processes:             117
  Usage of /:   21.6% of 77.35GB   Users logged in:       0
  Memory usage: 50%                IPv4 address for eth0: 134.209.172.50
  Swap usage:   0%                 IPv4 address for eth0: 10.17.0.5

Expanded Security Maintenance for Applications is not enabled.

11 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


*** System restart required ***
Last login: Wed Feb  4 19:30:29 2026 from 82.167.50.246
naltuwajiri@master-node:~$ source /etc/profile.d/hadoop.sh
naltuwajiri@master-node:~$ mapred streaming \
  -files mapper_task4.py,reducer_sum.py \
  -mapper "python3 mapper_task4.py" \
  -reducer "python3 reducer_sum.py" \
  -input /data/chicago_crimes_sample.csv \
  -output /user/naltuwajiri/task4_output
packageJobJar: [] [/opt/hadoop-3.4.1/share/hadoop/tools/lib/hadoop-streaming-3.4.1.jar] /tmp/streamjob799357668694777604.jar tmpDir=null
2026-03-18 04:12:49,626 INFO client.DefaultNoHARMFailoverProxyProvider: Connecting to ResourceManager at master-node/134.209.172.50:8032
2026-03-18 04:12:50,107 INFO client.DefaultNoHARMFailoverProxyProvider: Connecting to ResourceManager at master-node/134.209.172.50:8032
2026-03-18 04:12:50,744 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /tmp/hadoop-yarn/staging/naltuwajiri/.staging/job_1771402826595_0095
2026-03-18 04:12:52,572 INFO mapred.FileInputFormat: Total input files to process : 1
2026-03-18 04:12:53,189 INFO mapreduce.JobSubmitter: number of splits:2
2026-03-18 04:12:54,111 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1771402826595_0095
2026-03-18 04:12:54,111 INFO mapreduce.JobSubmitter: Executing with tokens: []
2026-03-18 04:12:54,363 INFO conf.Configuration: resource-types.xml not found
2026-03-18 04:12:54,364 INFO resource.ResourceUtils: Unable to find 'resource-types.xml'.
2026-03-18 04:12:54,467 INFO impl.YarnClientImpl: Submitted application application_1771402826595_0095
2026-03-18 04:12:54,513 INFO mapreduce.Job: The url to track the job: http://master-node:8088/proxy/application_1771402826595_0095/
2026-03-18 04:12:54,515 INFO mapreduce.Job: Running job: job_1771402826595_0095
2026-03-18 04:13:12,409 INFO mapreduce.Job: Job job_1771402826595_0095 running in uber mode : false
2026-03-18 04:13:12,412 INFO mapreduce.Job:  map 0% reduce 0%
2026-03-18 04:13:30,045 INFO mapreduce.Job:  map 100% reduce 0%
2026-03-18 04:13:40,981 INFO mapreduce.Job:  map 100% reduce 100%
2026-03-18 04:13:45,027 INFO mapreduce.Job: Job job_1771402826595_0095 completed successfully
2026-03-18 04:13:45,330 INFO mapreduce.Job: Counters: 54
        File System Counters
                FILE: Number of bytes read=90006
                FILE: Number of bytes written=1123265
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=2391502
                HDFS: Number of bytes written=185
                HDFS: Number of read operations=11
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=2
                HDFS: Number of bytes read erasure-coded=0
        Job Counters
                Launched map tasks=2
                Launched reduce tasks=1
                Data-local map tasks=2
                Total time spent by all maps in occupied slots (ms)=62002
                Total time spent by all reduces in occupied slots (ms)=16020
                Total time spent by all map tasks (ms)=31001
                Total time spent by all reduce tasks (ms)=8010
                Total vcore-milliseconds taken by all map tasks=31001
                Total vcore-milliseconds taken by all reduce tasks=8010
                Total megabyte-milliseconds taken by all map tasks=15872512
                Total megabyte-milliseconds taken by all reduce tasks=4101120
        Map-Reduce Framework
                Map input records=10001
                Map output records=10000
                Map output bytes=70000
                Map output materialized bytes=90012
                Input split bytes=212
                Combine input records=0
                Combine output records=0
                Reduce input groups=24
                Reduce shuffle bytes=90012
                Reduce input records=10000
                Reduce output records=24
                Spilled Records=20000
                Shuffled Maps =2
                Failed Shuffles=0
                Merged Map outputs=2
                GC time elapsed (ms)=578
                CPU time spent (ms)=3220
                Physical memory (bytes) snapshot=646995968
                Virtual memory (bytes) snapshot=6557986816
                Total committed heap usage (bytes)=348164096
                Peak Map Physical memory (bytes)=250306560
                Peak Map Virtual memory (bytes)=2184486912
                Peak Reduce Physical memory (bytes)=148787200
                Peak Reduce Virtual memory (bytes)=2190090240
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=2391290
        File Output Format Counters
                Bytes Written=185
2026-03-18 04:13:45,336 INFO streaming.StreamJob: Output directory: /user/naltuwajiri/task4_output
naltuwajiri@master-node:~$ hdfs dfs -cat /user/naltuwajiri/task4_output/part-00000
2001    4
2002    2
2003    1
2004    6
2005    19
2006    4
2007    7
2008    16
2009    5
2010    5
2011    7
2012    9
2013    10
2014    16
2015    28
2016    20
2017    49
2018    28
2019    36
2020    25
2021    83
2022    135
2023    9446
2024    39
naltuwajiri@master-node:~$ hdfs dfs -cat /user/naltuwajiri/task4_output/part-00000 > task4_result.txt
naltuwajiri@master-node:~$ exit
logout
Connection to 134.209.172.50 closed.
PS C:\Users\Surface Pro\Downloads\chicago_project\chicago_project\src> scp naltuwajiri@134.209.172.50:~/task4_result.txt .
naltuwajiri@134.209.172.50's password:
task4_result.txt                                                                                          100%  185     0.4KB/s   00:00
PS C:\Users\Surface Pro\Downloads\chicago_project\chicago_project\src>
```
 Task 5: Arrest Analysis
-
  Command
-
```bash
mapred streaming \
  -files mapper_task5.py,reducer_sum.py \
  -mapper "python3 mapper_task5.py" \
  -reducer "python3 reducer_sum.py" \
  -input /data/chicago_crimes_sample.csv \
  -output /user/ldardeer/task5_output
```
  Sample Output
-
```
false  8717
true   1283
```
  Interpretation
-
Most crimes do not result in an arrest, showing a significantly higher number of unresolved cases.

  Execution Logs
-
```
Last login: Wed Feb  4 21:52:10 on ttys008

The default interactive shell is now zsh.
To update your account to use zsh, please run `chsh -s /bin/zsh`.
For more details, please visit https://support.apple.com/kb/HT208050.
Linas-MacBook-Pro:~ linadardeer$ cd /Users/linadardeer/Downloads/chicago_project
Linas-MacBook-Pro:chicago_project linadardeer$ cd src
Linas-MacBook-Pro:src linadardeer$ scp mapper_task5.py reducer_sum.py ldardeer@134.209.172.50:~/
ldardeer@134.209.172.50's password: 
mapper_task5.py                               100%  240     1.3KB/s   00:00    
reducer_sum.py                                100%  489     2.1KB/s   00:00    
Linas-MacBook-Pro:src linadardeer$ ssh ldardeer@134.209.172.50
ldardeer@134.209.172.50's password: 
Welcome to Ubuntu 22.04.5 LTS (GNU/Linux 5.15.0-170-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Wed Mar 18 03:59:36 UTC 2026

  System load:  0.01               Processes:             117
  Usage of /:   21.6% of 77.35GB   Users logged in:       0
  Memory usage: 50%                IPv4 address for eth0: 134.209.172.50
  Swap usage:   0%                 IPv4 address for eth0: 10.17.0.5

Expanded Security Maintenance for Applications is not enabled.

11 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


*** System restart required ***
Last login: Wed Feb  4 18:07:39 2026 from 2.88.129.116
ldardeer@master-node:~$ source /etc/profile.d/hadoop.sh
ldardeer@master-node:~$ mapred streaming \
  -files mapper_task5.py,reducer_sum.py \
  -mapper "python3 mapper_task5.py" \
  -reducer "python3 reducer_sum.py" \
  -input /data/chicago_crimes_sample.csv \
  -output /user/ldardeer/task5_output
packageJobJar: [] [/opt/hadoop-3.4.1/share/hadoop/tools/lib/hadoop-streaming-3.4.1.jar] /tmp/streamjob358488507616051269.jar tmpDir=null
2026-03-18 04:13:22,490 INFO client.DefaultNoHARMFailoverProxyProvider: Connecting to ResourceManager at master-node/134.209.172.50:8032
2026-03-18 04:13:22,827 INFO client.DefaultNoHARMFailoverProxyProvider: Connecting to ResourceManager at master-node/134.209.172.50:8032
2026-03-18 04:13:23,347 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /tmp/hadoop-yarn/staging/ldardeer/.staging/job_1771402826595_0096
2026-03-18 04:13:25,158 INFO mapred.FileInputFormat: Total input files to process : 1
2026-03-18 04:13:25,841 INFO mapreduce.JobSubmitter: number of splits:2
2026-03-18 04:13:26,724 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1771402826595_0096
2026-03-18 04:13:26,724 INFO mapreduce.JobSubmitter: Executing with tokens: []
2026-03-18 04:13:27,095 INFO conf.Configuration: resource-types.xml not found
2026-03-18 04:13:27,096 INFO resource.ResourceUtils: Unable to find 'resource-types.xml'.
2026-03-18 04:13:27,285 INFO impl.YarnClientImpl: Submitted application application_1771402826595_0096
2026-03-18 04:13:27,343 INFO mapreduce.Job: The url to track the job: http://master-node:8088/proxy/application_1771402826595_0096/
2026-03-18 04:13:27,348 INFO mapreduce.Job: Running job: job_1771402826595_0096
2026-03-18 04:14:05,332 INFO mapreduce.Job: Job job_1771402826595_0096 running in uber mode : false
2026-03-18 04:14:05,334 INFO mapreduce.Job:  map 0% reduce 0%
2026-03-18 04:14:23,453 INFO mapreduce.Job:  map 100% reduce 0%
2026-03-18 04:14:35,385 INFO mapreduce.Job:  map 100% reduce 100%
2026-03-18 04:14:39,325 INFO mapreduce.Job: Job job_1771402826595_0096 completed successfully
2026-03-18 04:14:39,594 INFO mapreduce.Job: Counters: 54
	File System Counters
		FILE: Number of bytes read=98723
		FILE: Number of bytes written=1140582
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=2391502
		HDFS: Number of bytes written=21
		HDFS: Number of read operations=11
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=2
		HDFS: Number of bytes read erasure-coded=0
	Job Counters 
		Launched map tasks=2
		Launched reduce tasks=1
		Data-local map tasks=2
		Total time spent by all maps in occupied slots (ms)=60724
		Total time spent by all reduces in occupied slots (ms)=17078
		Total time spent by all map tasks (ms)=30362
		Total time spent by all reduce tasks (ms)=8539
		Total vcore-milliseconds taken by all map tasks=30362
		Total vcore-milliseconds taken by all reduce tasks=8539
		Total megabyte-milliseconds taken by all map tasks=15545344
		Total megabyte-milliseconds taken by all reduce tasks=4371968
	Map-Reduce Framework
		Map input records=10001
		Map output records=10000
		Map output bytes=78717
		Map output materialized bytes=98729
		Input split bytes=212
		Combine input records=0
		Combine output records=0
		Reduce input groups=2
		Reduce shuffle bytes=98729
		Reduce input records=10000
		Reduce output records=2
		Spilled Records=20000
		Shuffled Maps =2
		Failed Shuffles=0
		Merged Map outputs=2
		GC time elapsed (ms)=622
		CPU time spent (ms)=3130
		Physical memory (bytes) snapshot=668512256
		Virtual memory (bytes) snapshot=6571532288
		Total committed heap usage (bytes)=347955200
		Peak Map Physical memory (bytes)=263532544
		Peak Map Virtual memory (bytes)=2186780672
		Peak Reduce Physical memory (bytes)=155320320
		Peak Reduce Virtual memory (bytes)=2198073344
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=2391290
	File Output Format Counters 
		Bytes Written=21
2026-03-18 04:14:39,595 INFO streaming.StreamJob: Output directory: /user/ldardeer/task5_output
ldardeer@master-node:~$ hdfs dfs -cat /user/ldardeer/task5_output/part-00000
false	8717
true	1283
ldardeer@master-node:~$ hdfs dfs -cat /user/ldardeer/task5_output/part-00000 > task5_result.txt
ldardeer@master-node:~$ exit
logout
Connection to 134.209.172.50 closed.
Linas-MacBook-Pro:src linadardeer$ scp ldardeer@134.209.172.50:~/task5_result.txt .
ldardeer@134.209.172.50's password: 
task5_result.txt                              100%   21     0.1KB/s   00:00    
Linas-MacBook-Pro:src linadardeer$
```
 Contribution
-
Mappers: Alanoud & Masa

Reducers: Lina & Noura
