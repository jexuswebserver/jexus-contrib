| Features | IIS 7+ | Jexus 5 | Differences | 
| -------- | ------ | ------- | ----------- |
| ASP.NET Web Forms | Complete | Complete | Jexus is affected by Mono limitations. [*] |
| ASP.NET MVC	| Complete | Complete | Jexus is affected by Mono limitations. [*] |
| ASP.NET Web API | Complete | Complete | Jexus is affected by Mono limitations. [*] |
| WCF | Complete | Complete | Not all WCF features are supported by Mono. |
| Application pool | Complete | [Partly](http://www.lextm.com/2013/10/jexus-series-application-pool-setting/) | Jexus supports one pool only. [**] |
| Web Garden | Complete | [Partly](http://www.lextm.com/2013/10/jexus-series-application-pool-setting/) | Jexus supports up to 8 worker processes. | 
| URL Rewrite | Complete (via OOB installer) | [Partly](http://www.lextm.com/2013/10/jexus-series-url-rewrite/) | Jexus does not support outbound rules. [***] |
| Reverse proxy | Complete (via OOB installer of ARR) | Complete | |
| IP address restriction | Complete | [Complete](http://www.lextm.com/2013/10/jexus-series-ip-and-domain-restrictions/) | Jexus does not support dynamic IP restriction. |
| Request filtering | Complete | Partly | Jexus only supports a few checks. |
| FastCGI | Complete | Complete | |
| HTTPS | Complete | Partly | Jexus does not have SNI support yet. |
| Output caching | Complete | Partly | Jexus output caching must be enabled at page level. |
| Media Streaming | Windows Media formats only | Flash based formats only | |
| Smooth Streaming | Complete | Partly | Jexus does not support live streaming. |
| Logging | Complete | Partly | Jexus currently only logs to files. |
| IIS Manager | Complete | Jexus Manager is in development.[****] | |
| Extensibility | Complete | No | |
| Failed Request Tracing | Complete | No | |
| Other IIS features | Complete | No | |

[*]: Mono 3.2 is recommended, in which the Mono guys fixed most known issues.

[**]: Other differences include but not limited to,

1. Compared to IIS, Jexus uses a built-in algorithm to perform ping instead of providing related settings.

1. Jexus worker process is fully managed.

1. IIS has a lot of settings to define when to recycle worker processes, while Jexus (5.5+) supports 2 settings, `httpd.MaxTotalMemory` and `httpd.MaxCpuTime`.

[***]: Other differences include,
1. Jexus does not support actions such as Redirect or AbortRequest.

1. Jexus does not support conditions.

1. Jexus cannot break from cascading rules.

[****]: Jexus Manager is currently in 0.5 and is in private beta testing by a small group of Jexus users. It looks similar to IIS Manager, and utilizes an agent installed on Jexus machine to achieve remote management.

* Jexus Manager is a Windows Forms based application that can run on any Windows/Linux/OS X machines with .NET Framework or Mono installed.
* Jexus Manager Remote Services agent is a console application that must be installed together with Jexus web server on any Linux/FreeBSD machines, which Jexus Manager connects to read/write Jexus configuration.
