# Ex 1. Realtime Traffic Map
This is a high-level view map developed for executive audience. It is a realtime traffic map showing the company hubsite cities, circuit IDs in between along with bandwidth and total utilization per segment, and link state. It is possible to select previous date/time and retrieve network information at the chosen time.

![highlevel](/assets/high-level-ipcore.png)

# Ex 2. Congestion and Failover Reports
Here are several screenshots from an interactive tool developped for network engineers, with the objective of facilitating traffic growth monitoring and capacity planning activities. The menu on top of each page indicates the different dashboards.

### Network Logical View
First, we show a logical view of the ISP network topology, with routers at hibsites and logical links in between. A color-code is used to differentiate ISP ownership of fibers and leased, as well as links avaiability in the event of failure (e.g. fiber cut). This is not shown for privacy constraints, but upon hovering over a link it provides such realtime information as end routers and interfaces, bandwidth and traffic on the link in question. Clicking on the link opens another window showing historical trend for the given link. \[Note that router names have been blured for privacy purposes.\]

![logical](/assets/logical-map.png)

### Network Geographical View
The previous network is represented below, but from a geographic perspective. This allows network engineers to quickly identify circuits that are sharing fiber and where they do so. Other functionalities are the same as for the logical view, and again router names are blured for privacy purposes. 

![geographical](/assets/geo-map.png)

### Congestion Table
Another key tab

![congestion](/assets/congestion.png)

### Failover Table
...

![failover](/assets/failover.png)

### Historical Trends
...

![trendW](/assets/trend-id-weekly.png)

![trendY](/assets/trend-id-year.png)

# Ex 3. Devices & Ports Tracking
...

![operations](/assets/device-ports.png)
