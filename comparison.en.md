| Features | IIS 7+ | Jexus 5 | Differences | 
| -------- | ------ | ------- | ----------- |
| Application pool | Complete | Partly | Jexus supports one pool only. |
| Web Garden | Complete | Partly | Jexus supports up to 8 worker processes. | 
| URL Rewrite | Complete (via OOB installer) | Complete | Configuration method is different. |
| Reverse proxy | Complete (via OOB installer of ARR) | Partly | Jexus does not support outbound rules. |
| Request filtering | Complete | Partly | Jexus only supports a few checks. |
| FastCGI | Complete | Complete | |
| HTTPS | Complete | Partly | Jexus does not have SNI support yet. |
| Output caching | Complete | Partly | Jexus output caching must be enabled at page level. |
| Media Streaming | Windows Media formats only | Flash based formats only | |
| Smooth Streaming | Complete | Partly | |
| ASP.NET Web Forms | Complete | Complete | |
| ASP.NET MVC	| Complete | Complete | |
| ASP.NET Web API | Complete | Complete | |
| WCF | Complete | Partly | Jexus does not support all WCF features due to Mono limitations. |
| Logging | Complete | Partly | Jexus currently only logs to files. |
| IIS Manager | Complete | No | |
| Extensibility | Complete | No | |
| Failed Request Tracing | Complete | No | |
| Other IIS features | Complete | No | |

