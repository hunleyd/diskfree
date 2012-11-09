diskfree
========

Bash script for reporting on disk usage and growth

Usage
-----
diskfree [-p] [-m email_address] [-v] [-l logdir] [-r] [-d dirs]
<br>  -p - 'I am a paranoid admin' mode. Report on entire directory tree
<br>  -m - email address to send report to (or '@' to print to stdout)
<br>  -l - specify directory to store log files in (Default: /tmp)
<br>  -e - special extension to append to output
<br>  -v - print version info and exit
<br>  -r - create and mail report even if empty (so you know it ran)
<br>  -d - report on specified directories instead of subdirectories of /

  diskfree is a simple self-contained Bash script I wrote to keep track of disk usage
  on a given machine. You simply drop it into /etc/cron.daily and then it will email
  you daily reports showing both the disk usage of the machine as well as a listing
  of what directories have changed/shrunk since the last time it ran.

  You can choose to monitor specific directoris (say, /home) if you don't like the
  default behavior of monitoring everything. Simply use the '-d' option. By default,
  you get a report on the top-level directories only, but adding '-p' will give an
  exhaustive listing of everything under the reported path.

  Additionally, you can use the '-e' option to make differential reports. For example,
  you could use '-e daily' for cron.daily runs and '-e weekly' for cron.weekly run and
  you'd get reports of changes daily and weekly, respectively.

Requirements
------------
GNU Bash
<br>GNU coreutils

Example Output
--------------
  <pre>
  Total allocations
  Filesystem      Size  Used Avail Use% Mounted on
  /dev/sda3       465G   17G  430G   4% /
  /dev/sda1        47M   20M   24M  46% /boot
  /dev/sdb1       466G  242G  209G  54% /home

  Changed allocations
  /home/doug/foo is 10M was 0
  </pre>

Bugs
----
Find a bug? Please create an issue here on GitHub at:
https://github.com/hunleyd/diskfree/issues

Twitter
-------
Keep up to data on announcements and more by following Doug on Twitter, <a href="http://twitter.com/hunleyd">@hunleyd</a>

Authors
-------
**Douglas J Hunley**
+ G+: http://goo.gl/sajR3
+ Twitter: http://twitter.com/hunleyd
+ GitHub: http://github.com/hunleyd

Copyright and license
---------------------
Copyright 2012 Douglas J Hunley.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this work
except in compliance with the License. You may obtain a copy of the License in the
LICENSE file, or at:

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the
License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
either express or implied. See the License for the specific language governing
permissions and limitations under the License.
