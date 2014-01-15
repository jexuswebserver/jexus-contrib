   
README for Jexus Web Server 5.5
---------------------------------

Jexus is a web server for Linux/UNIX operating systems, which serves ASP.NET web sites and applications. It is free (free as beer) and has an IIS alike architecture with high performance and stability, as well as the following features,

* First class ASP.NET support.
* Complete Fast-CGI support (for PHP and other technologies).
* Output caching support.
* Reverse proxy support.
* URL rewrite support.
* Media streaming support for Flash based media files (FLV and F4V)
* IIS Smooth Streaming support.
* HTTPS support.
* Built-in attack prevention mechanism.
* Simple installation and management.

Installation
------------

The following steps assume that you use latest Ubuntu Linux distro.

####1. Install Mono runtime.
`sudo apt-get install mono-complete`

> As Jexus requires Mono runtime, in this step we install latest stable Mono runtime via apt-get. 
> For most Linux distros, 2.10.* is still the version in package repository. Jexus can work with such obsolete Mono versions, but the latest stable Mono (3.2.*) is highly recommended.
> Please refer to the documentation of the specific distro if you don't know how to install Mono.

####2. Downloadn and unpack Jexus
```
wget http://www.linuxdot.net/down/jexus-5.5.tar.gz
tar -zxvf jexus-5.5.tar.gz
```

> Jexus binary package is downloaded from its official site, and extracted to a folder named “jexus-5.5″ after this step.

####3. Create default web site

1. `sudo vi /var/www/default/index.html`
2. Press i on keyboard to enter edit mode.
3. Type “Hello World from Jexus” and press Esc on keyboard to exit edit mode.
4. Type :wq and press Enter on keyboard to exit vi.

> /var/www/default is the default web site path for Jexus. In this step we create a test page using gedit. You might use any other Linux text editor to create this test page.

####4. Install and launch Jexus
```
cd jexus-5.5
sudo ./install
cd /usr/jexus
sudo ./jws start
```

> Here we put Jexus binary to /usr/jexus folder, grant the jws shell script file execution permission, and then use it to register Jexus modules in Mono GAC and launch the HTTP service. If you want to install Jexus to another location, please change the commands accordingly.

Now if we open Firefox and navigate to http://localhost, the test page we created is displayed correctly,

Screenshot
http://flic.kr/p/ghCfmG 
Jexus test page in Firefox

Upgrade
-------
####1. Download and unpack Jexus
```
wget http://www.linuxdot.net/down/jexus-5.5.tar.gz
tar -zxvf jexus-5.5.tar.gz
```
> Jexus binary package is downloaded from its official site, and extracted to a folder named “jexus-5.5″ after this step.

####2. Stop old Jexus server,
```
cd /usr/jexus
sudo ./jws stop
```
Note that if the old Jexus in use is of version 5.2 and below, the second command should be changed to `sudo ./jws.stop`.

####3. Copy new files to Jexus folder
```
cd ~/jexus-5.5
sudo ./upgrade
```

> Now let’s go back to the extracted folder and upgrade necessary files to /usr/jexus.

####4. Fix startup commands
1. `sudo vi /etc/rc.local`
2. Press i on keyboard to enter edit mode.
3. Replace previous start command “/usr/jexus/jws.start” with “/usr/jexus/jws start”. (Needed only old Jexus is 5.2 and below).
4. Remove “/usr/jexus/state.start” if it presents.
5. Press Esc on keyboard to exit edit mode.
6. Type :wq and press Enter on keyboard to exit vi.

####5. Start Jexus HTTP service
```
cd /usr/jexus 
sudo ./jws start
```

Configuration System
--------------------
Jexus currently uses configuration format similar to Apache/Nginx.

####Server Configuration
The configuration file, which contains most of Jexus settings, is located in Jexus installation folder (usually /usr/jexus) and named jws.conf.

Unlike IIS which uses XML to store settings, the Jexus settings are stored in key-value pair, for example

```
SiteLogDir=log
SiteConfigDir=siteconf
```

Note that any change to server configuration only takes effect when Jexus is restarted.

The description of each settings is listed as below,

| Setting | Mandatory? | Description |
| ------- | ---------- | ----------- |
| SiteConfigDir | yes | The directory that holds web site configuration files. Relative paths to jws.exe can be used. |
| SiteLogDir | yes | The directory that holds the log files. Relative paths to jws.exe can be used. |
| Runtime | no | Application pool ASP.NET runtime version. For example, `Runtime=v4.0.30319` or `Runtime=v4.0`. |
| httpd.processes | no | Specifies the number of worker processes associated with the application pool. A value other than 1 indicates a Web garden. The default value is 1. |
| httpd.user | no | Application pool identity. For example, `httpd.user=www-data`. |
| httpd.MaxTotalMemory | no | (5.5+) Specifies the maximum total physical memory (of MBytes) that all worker processes can consume before the pool starts to recycle worker processes. It ranges from `256` to 80% of maximum physical memory installed on the machine. The default is `0`, where Jexus automatically adjusts the usage. Note that for each worker process the minimum physical memory usage is 128-MBytes. |
| httpd.MaxCpuTime | no | (5.5+) Specifies how much CPU resources (of seconds) can be consumed by a single worker process before being recycled by the pool. It ranges from `600` to `14400`. The default value is `3600`. |
| LLVM | no | When a worker process is created, [Jexus passes this flag to Mono](http://www.mono-project.com/Mono:Runtime:Documentation:LLVM). The default value is false. | 

The first two settings are mandatory.

The log directory must give Jexus process permissions to write, as Jexus server log and web site access logs are all generated and stored there.

In default installation, /usr/jexus/siteconf is used as configuration directory, while /usr/jexus/log is used as log directory.

####Web Site Configuration

Jexus supports multiple web sites running on the same server. The web sites use individual bindings to distinguish from each other.

The web site configuration files must be saved in the configuration directory set in jws.conf (aka SiteConfigDir). The configuration file name is used as site name (site name is only used in Jexus commands), which should not contain spaces. Note that all files in configuration directory are treated as web site configuration files. Thus, don’t leave anything else there.

Note that any change to web site configuration only takes effect when the web site is restarted.

In default installation, a default web site is created. Its configuration file is /usr/jexus/siteconf/default. Just like jws.conf, the web site configuration is also stored in key value pair, and the description of each settings is as below,

| Setting | Mandatory? | Description |
| ------- | ---------- | ----------- |
| addr | no | The web site IP address. Default is `addr=0.0.0.0`. (no IP v6 support yet) |
| port | yes | The port number used for this web site. Default is `port=80`. |
| hosts | no | The host header accepted by this web site. Default is `hosts=*`, which means any host header is accepted. Wildcard is also supported, such as *.mysite.com. |
| root | yes | The directory mapping. The default is `root=/ /var/www/default`, which maps physical directory  /var/www/default that contains the web site contents to web site root. |
| indexes | no | Default document name list. For example, when `indexes=index.aspx,index.htm` is used, access to / will be resolved to index.aspx if it exists, and then index.htm if exists, and 404 if none of them exists. When this setting is not set, Jexus uses its built-in name list. See (*1)for more details. |
| rewrite | no | URL rewrite rule. For example, <code>rewrite=^/.+?\.(asp&#124;php&#124;cgi)$ /404.html</code> means any access to classic ASP/PHP/CGI pages is rewritten to /404.html. To use multiple rules, use multiple lines of `rewrite=`. | 
| denyfrom | no | IP address restriction. For example, when `denyfrom=111.222.111.*,1.1.1.1` is used, access from the IP addreses are denied. Mask is also supported, such as `denyfrom=192.168.1.0/255.255.255.0`. |
| allowfrom | no | IP address restriction. For example, when `allowfrom=111.222.111.*,1.1.1.1` is used, only access from the IP addresses are allowed. All other access is denied. |
| DenyDirs | no | Hidden segments. When `DenyDirs=bin,App_code` is used, access to such URL paths is denied. |
| checkquery | no | Query strings restriction. Jexus uses built-in logic to perform query safety check. The default is `checkquery=true`. Note that by setting this to true, there is some impact on Jexus performance. |
| nofile | no | NOFILE is a Jexus specific feature. It is similar to IIS custom error pages for 404. When `nofile=/mvc/controller.aspx` is used, access to non-existent files is redirected to /mvc/controller.aspx. Note that the original URL is passed via X-Real-Uri server variable. |
| nolog | no | Logging flag. The default is `nolog=false`. When set to true, Jexus stops generating log files for this web site. |
| keep\_alive | no | HTTP keep-alive flag. The default is `keep_alive=true`. | 
| reproxy | no | Reverse proxy rule. When `reproxy=/abc/ http://www.xxxx.com:890/abc/` is used, requests on /abc/ (source) will be redirected to http://www.xxxx.com:890/abc/ (destination). The destination can be multiple, so that Jexus randomly picks one from them, which is similar to load balancing. For example, `reproxy=/abc/ http://192.168.0.3/abc/,http://192.168.0.4/abc/`. |
| fastcgi.add | no | FastCGI rule. For TCP connections, typical setting is `fastcgi.add=php,php3|tcp:127.0.0.1:9000`, which forwards requests of .php or php3 extensions to 127.0.0.1:9000 via TCP. For UNIX sockets, typical setting is `fastcgi.add=php,php3|socket:/tmp/phpsvr` 
| usegzip | no | GZip compression flag. The default is `usegzip=true`. |
| usehttps | no | SSL flag. To enable HTTPS, this setting must be set to true, and port must be set to 443 at the same time. The default is `usehttps=false`. See (*2) for more details. |

*1 The Jexus built-in default document name list is as below,
* index.aspx
* Index.aspx
* default.aspx
* Default.aspx
* index.htm5.4
* Index.htm
* default.htm
* Default.htm
* index.html
* Index.html
* default.html
* Default.html
* index.php
* Index.php
* default.php
* Default.php

*2 To enable HTTPS, please follow the steps in this blog post.

Management Script and Commands
------------------------------
Starting from Jexus 5.3 the commands are merged into one Shell script, /usr/jexus/jws.

This script provides the following functionality,

| Command | Description |
| ------- | ----------- |
| jws start | Start Jexus server. |
| jws start site\_name | Start a single web site. Note that site_name must match one of the configuration files under configuration directory. |
| jws restart | Restart Jexus server. |
| jws restart site_name | Restart a single web site. |
| jws stop | Stop Jexus server. |
| jws stop site_name | Stop a single web site. |
| jws regsvr | Register Jexus assembly in GAC. Note that this is only required to be executed once during installation. 
| jws status | Report Jexus runtime status. |
| jws -v | Display Jexus version number. |

The script should be set to executable during installation. The commands can only be executed by root.

Questions on Jexus can be posted to https://github.com/jexuswebserver/jexus-contrib/issues.
