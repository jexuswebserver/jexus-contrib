| Features | IIS 7+ | Jexus 5 | Differences | 
| -------- | ------ | ------- | ----------- |
| ASP.NET Web Forms | Complete | Complete | Jexus is affected by Mono limitations. [*] |
| ASP.NET MVC	| Complete | Complete | Jexus is affected by Mono limitations. [*] |
| ASP.NET Web API | Complete | Complete | Jexus is affected by Mono limitations. [*] |
| WCF | Complete | Complete | Not all WCF features are supported by Mono. |
| Application pool | Complete | Partly | Jexus supports one pool only. [**] |
| Web Garden | Complete | Partly | Jexus supports up to 8 worker processes. | 
| URL Rewrite | Complete (via OOB installer) | Complete | Jexus does not support outbound rules. |
| Reverse proxy | Complete (via OOB installer of ARR) | Complete | |
| IP address restriction | Complete | Complete | Jexus does not support dynamic IP restriction. |
| Request filtering | Complete | Partly | Jexus only supports a few checks. |
| FastCGI | Complete | Complete | |
| HTTPS | Complete | Partly | Jexus does not have SNI support yet. |
| Output caching | Complete | Partly | Jexus output caching must be enabled at page level. |
| Media Streaming | Windows Media formats only | Flash based formats only | |
| Smooth Streaming | Complete | Partly | Jexus does not support live streaming. |
| Logging | Complete | Partly | Jexus currently only logs to files. |
| IIS Manager | Complete | No | |
| Extensibility | Complete | No | |
| Failed Request Tracing | Complete | No | |
| Other IIS features | Complete | No | |

*: Mono 3.2 is recommended, in which the Mono guys fixed most known issues.
**: Other differences include but not limited to,
1. Compared to IIS, Jexus uses a built-in algorithm to perform ping instead of providing related settings.
2. Jexus worker process is fully managed.
