# munin-plugin-Oracle-DRCP
Must use Oracle DRCP and Munin

#install
<pre>
cpanm DBD::Oracle
</pre>

#Contains
<pre>
oracle_drcp_listener_perSec       Number of DRCP connections per sec that Listeners have allowed
oracle_drcp_deny_listener_perSec  Number of DRCP connections per sec that Listeners have denied
oracle_drcp_Open_Busy_Servers     Number of DRCP OPEN SERVERS and BUSY SERVERS
oracle_drcp_Requests_WaitsIn5Mins Number of DRCP Requests and Waits
</pre>
#settings
<pre>
if ( hostname() eq 'HOSTNAME' ) { #HOSTNAME
	$ENV{"ORACLE_HOME"} = "/opt/app/oracle/product/11.2.0.4/dbhome_1"; #ORACLE_HOME
	$COUNTLISTENER=1; #LISTER COUNT(Listener names must be LISTENER and LISTENER2 and so on)
	$CBROK=1; #Count of Num_Cbrok
	$ST=1; #start listerner number. if DRCP use LISTENER 3 and 4 and 5,$ST=3 
}

or

if ( hostname() eq 'HOSTNAME' ) {
  $ENV{'ORACLE_HOME'} = '/opt/app/oracle/product/11.2.0/dbhome_1';
  $ENV{'LD_LIBRARY_PATH'} = '/opt/app/oracle/product/11.2.0/dbhome_1/lib';
  $dbhost = '127.0.0.1';
  $dbname = 'SID';
  $dbuser = 'system';
  $dbport = '1521';
  $dbpass = 'PASSWORD';
  $dsn = "DBI:Oracle:$dbname";
}
</pre>

#sample
<pre>
$ munin-run oracle_drcp_listener_perSec
listener3N000.value 0
listener3N001.value 0
listener4N000.value 0
listener4N001.value 0
listener5N000.value 0
listener5N001.value 0

$ munin-run oracle_drcp_Open_Busy_Servers
OpenServers.value 150
BusyServers.value 0

$ munin-run oracle_drcp_Requests_WaitsIn5Mins
NumRequests.value 0
NumWaits.value 0
</pre>
