| Features | IIS 7+ | Jexus 5 | Differences | 
| -------- | ------ | ------- | ----------- |
| ASP.NET Web Forms | Complete | Complete | Jexus is only limited by Mono. |
| ASP.NET MVC	| Complete | Complete | Jexus is only limited by Mono. |
| ASP.NET Web API | Complete | Complete | Jexus is only limited by Mono. |
| WCF | Complete | Complete | Not all WCF features are supported by Mono. |
| Application pool | Complete | Partly | Jexus supports one pool only. |
| Web Garden | Complete | Partly | Jexus supports up to 8 worker processes. | 
| URL Rewrite | Complete (via OOB installer) | Complete | Configuration method is different. |
| Reverse proxy | Complete (via OOB installer of ARR) | Partly | Jexus does not support outbound rules. |
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

