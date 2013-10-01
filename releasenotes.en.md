Release Notes for Jexus Web Server
----------------------------------

####Version 5.3
Released on May 11, 2013
1. Fixed "Chinese characters in request path or query string can not be resolved correctly" bug in reverse proxy module.
2. Fixed "pathinfo is lost" bug.
3. Improved HTTPS support.
4. (Breaking) ASP.NET State Service is now incorporated into Jexus master service process to simplify management;
5. (Breaking) Added a single command "jws" to replace individual commands like "jws.start", "jws.stop".


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



