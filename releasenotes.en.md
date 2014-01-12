Release Notes for Jexus Web Server
----------------------------------

####Version 5.5
Released on Jan 12, 2014

1. Fixed "ASP.NET log entry might be incomplete" bug in logging.
2. Added two settings in server configuration, `httpd.MaxTotalMemory` and `httpd.MaxCpuTime`.
3. Added `app_offline.htm` support.

####Version 5.4.4
Released on Oct 1, 2013

1. Maximum number of worker processes is increased to [number of CPU cores] + 1 (still need to be <= 8).
2. Maximum connections are now dynamically adjusted to avoid file descriptor exhaustion.
3. Enabled TCP\_DEFER\_ACCEPT option at TCP layer.
4. Fixed "cannot find all hang worker processes" bug in application pool ping.
5. Fixed "Range: byte=0-x is not properly processed" bug in Range header processing.
6. Fixed "ASP.NET module cannot get external port number in NAT setup where external and internal port numbers differ" bug.

####Version 5.4
Released on July 1, 2013

1. Added application pool ping support.
2. Added a new option to change socket listener binding from default to a certain IP address.
3. Added a new option to control IP address whitelist.

####Version 5.3
Released on May 11, 2013

1. Fixed "Chinese characters in request path or query string can not be resolved correctly" bug in reverse proxy module.
2. Fixed "pathinfo is lost" bug.
3. Improved HTTPS support.
4. (Breaking) ASP.NET State Service is now incorporated into Jexus master service process to simplify management;
5. (Breaking) Added a single command "jws" to replace individual commands like "jws.start", "jws.stop".
6. Core thread pool is optimized.

####Version 5.2
Released on Jan 21, 2013

1. FastCGI and reverse proxy modules now support multiple cookies.
2. Added chunked transfer encoding support.
3. Improved support for files with Chinese names mangled on Linux after copying from Windows.
4. ASP.NET module now has OPTIONS/PUT/DELETE verbs enabled to support Web API projects.
5. Improved data transmission method used in application pool control and cross app domain communication. Boosted static file performance by 5% and ASP.NET by 40%.
6. Other bug fixes.

####Version 5.1
Released on Sept 19, 2013

1. Added FastCGI support.
2. Improved overall performance.



