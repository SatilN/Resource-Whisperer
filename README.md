<html>
<head>
<meta content="text/html; charset=ISO-8859-1"
http-equiv="content-type">
</head>
<body>
<p class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">This
code monitors
various system performance metrics and displays them on a web
interface. Here's
a detailed explanation of each section:<o:p></o:p></span></p>
<p class="MsoNormal" style="line-height: normal;"><b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">1.
Imports:</span></b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"><o:p></o:p></span></p>
<ul type="disc">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">psutil</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: This
library retrieves information about CPU, memory, disk, and network
usage.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">time</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: This
library allows for pausing the script execution for a specific duration.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">platform</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: This
library provides information about the operating system (Windows,
Linux, macOS).<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">subprocess</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">
(optional): This library might be used to run external commands for
temperature retrieval on macOS.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">openpyxl</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: This
library handles reading, writing, and manipulating data in Excel files.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">datetime</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: This
library helps with working with timestamps for data logging.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">ctypes</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">
(Windows only): This library interacts with the Windows API for
temperature retrieval.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">os</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: This
library provides various operating system functionalities.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">Flask</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: This
is a lightweight web framework for creating web applications to display
the collected metrics.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">threading</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: This
library enables running the Flask app in a separate thread, allowing
for continuous performance monitoring.<o:p></o:p></span></li>
</ul>
<p class="MsoNormal" style="line-height: normal;"><b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">2.
Configuration:</span></b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"><o:p></o:p></span></p>
<ul type="disc">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">Thresholds
are defined for CPU, memory, disk, network usage, and temperature.
These values serve as benchmarks to identify potential performance
issues.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">The
script defines the location and filename for the Excel file where
performance metrics will be logged.<o:p></o:p></span></li>
</ul>
<p class="MsoNormal" style="line-height: normal;"><b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">3. Data
Collection
Functions:</span></b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"><o:p></o:p></span></p>
<ul type="disc">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">Various
functions are defined to retrieve specific system metrics: <o:p></o:p></span></li>
<ul type="circle">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">get_cpu_load</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Retrieves CPU usage percentage using </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">psutil.cpu_percent</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">get_memory_usage</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Retrieves memory usage percentage using </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">psutil.virtual_memory.percent</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">get_disk_usage</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Retrieves disk usage percentage using </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">psutil.disk_usage</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">get_network_usage</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Retrieves sent and received network bytes using </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">psutil.net_io_counters</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">get_temperature</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Attempts to retrieve temperature based on the operating system: <o:p></o:p></span></li>
<ul type="square">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">Windows:
Uses WMI (Windows Management Instrumentation) if administrator
privileges are available (</span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">wmi</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"> module
required).<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">Linux:
Uses </span><span style="font-size: 10pt; font-family: &quot;Courier New&quot;;">psutil.sensors_temperatures()</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">, which
might require additional configuration.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">macOS:
Relies on the </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">osx-cpu-temp</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"> tool
(needs separate installation).<o:p></o:p></span></li>
</ul>
</ul>
</ul>
<p class="MsoNormal" style="line-height: normal;"><b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">4. Data
Logging and
Alerting:</span></b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"><o:p></o:p></span></p>
<ul type="disc">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">log_to_excel</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: Logs
collected metrics (CPU, memory, disk, temperature, network) to the
specified Excel file along with a timestamp retrieved using </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">datetime.now()</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">check_alerts</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Compares collected metrics against defined thresholds and generates
alert messages if any thresholds are exceeded.<o:p></o:p></span></li>
</ul>
<p class="MsoNormal" style="line-height: normal;"><b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">5.
Performance
Monitoring:</span></b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"><o:p></o:p></span></p>
<ul type="disc">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">monitor_performance</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: This
function runs continuously at a defined interval (default 5 seconds)
using a </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">while True</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"> loop. <o:p></o:p></span></li>
<ul type="circle">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">Inside
the loop, it calls all data collection functions to get the latest
metrics.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">It logs
the metrics to the Excel file using </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">log_to_excel</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">It
checks for alerts based on thresholds using </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">check_alerts</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"> and
updates a global dictionary (</span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">latest_metrics</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">) with
current values and potential alerts.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">Finally,
it prints the collected metrics and any alerts to the console for
immediate feedback.<o:p></o:p></span></li>
</ul>
</ul>
<p class="MsoNormal" style="line-height: normal;"><b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">6. Web
Interface with
Flask:</span></b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"><o:p></o:p></span></p>
<ul type="disc">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">The
script utilizes Flask to create a simple web interface for users to
view the performance metrics: <o:p></o:p></span></li>
<ul type="circle">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">index.html</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">: This
HTML file defines the layout of the web page, including placeholders
for the dynamic content (metrics).<o:p></o:p></span></li>
</ul>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">Flask
routes: <o:p></o:p></span></li>
<ul type="circle">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">/</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Renders the </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">index.html</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">
template, passing the machine name as a variable.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">/metrics</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Returns the latest metrics data (CPU, memory, disk, temperature,
network, alerts, and file location) in JSON format. This data can be
used for dynamic updates on the web page using JavaScript.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">/download/&lt;filename&gt;</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Enables downloading the performance log Excel file from the specified
directory.<o:p></o:p></span></li>
</ul>
</ul>
<p class="MsoNormal" style="line-height: normal;"><b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">7.
Running the Script:</span></b><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"><o:p></o:p></span></p>
<ul type="disc">
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">run_flask</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Starts the Flask app in a separate thread using </span><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">threading.Thread</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;"> to
allow the web interface to remain accessible while performance
monitoring continues.<o:p></o:p></span></li>
<li class="MsoNormal" style="line-height: normal;"><span
style="font-size: 10pt; font-family: &quot;Courier New&quot;;">monitor_performance</span><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">:
Starts the continuous monitoring loop to collect and process system
metrics.<o:p></o:p></span></li>
</ul>
<p class="MsoNormal" style="line-height: normal;"><span
style="font-size: 12pt; font-family: &quot;Times New Roman&quot;,serif;">Overall,
this code
provides a valuable tool for monitoring system performance with data
logging to
an Excel file and a web interface for real-time visualization. If you
have any
further questions about specific parts of the code, feel free to ask!<o:p></o:p></span></p>
<p class="MsoNormal"><o:p>&nbsp;</o:p></p>
</body>
</html>

