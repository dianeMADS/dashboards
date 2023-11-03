The following dashboards are part of a family of core network reports aimed at providing insights on traffic volumes and subsequent resource requirements. The context is a service provider network with millions of users and a mix of all types of internet traffic. The network has hundreds of links with varied capacities, from multiple 10Gs for smaller hubsites to tens of 100Gs for backbone links. Link costs are also varied as some are on the service provider’s own fiber infrastructure while others are leases from other providers. Initial data sources are Network Management Systems (NMS) collecting 5-min traffic measurements from network routers and dumping them into a datalake. An ETL workflow is scheduled to differentiate and aggregate traffic traces on a daily, weekly, and monthly basis. Those are the data feeding the BI tool for use in dashboards.
##### Toolkit: (NMS) API, Python, SQL and key-value NoSQL, AWS cloud computing, Alteryx, SnowFlake, Tableau

## Ex 1. Realtime Traffic Map
One visualization is to give leadership a high-level view of the network topology and bandwidth utilization. It is a realtime traffic map showing: cities (i.e. network nodes), links with color coding differentiating between owned and leased fibers and failure events, and traffic over installed capacity in bits per sec. It is possible to select previous date/time and retrieve network information at the chosen time. Knowing network state at specific times, especially under critical conditions, facilitates discussions on growth requirements and network expansions. 

<!-- [Note cities and traffic/bandwith numbers are hidden for privacy purposes.] -->
<!-- ![highlevel](/assets/high-level-mpls.png)
-->

### Network Logical View
For example, the following dashboard presents a more interactive version of described maps. This shows a logical view of an IP backbone [hubsite names are hidden for privacy purposes.] Realtime information such as end-points and interfaces, bandwidth avialble and current utilization are shown when hovering over links. The map also allows to select a link (i.e. mouse click) and display historical trend for bandwidth and traffic carried on the given link (to be discussed later.)

![logical](/assets/logical-map.png)


<!--[hubsites  
, with routers at hubsites and logical links in between. A color-code is used to differentiate ISP ownership of fibers and leased, as well as links availability in the event of failure (e.g. fiber cut). This is not shown for privacy constraints, but upon hovering over a link it provides such realtime information as end routers and interfaces, bandwidth and traffic on the link in question. Clicking on the link opens another window showing historical trend for the given link. \[Note that router names have been blured for privacy purposes.\] -->


### Network Geographical View
The previous network is represented below, but from a geographic perspective. This allows network engineers to quickly identify circuits that are sharing fiber and where they do so. Other functionalities are the same as for the logical view, and again router names are blured for privacy purposes. 
![geographical](/assets/geo-map.png)


Main Tools: SQL, AWS (Athena & S3), Alteryx, SnowFlake, Tableau

## Ex 2. Congestion and Failover Reports
Other dashboards comprise congestion and failover tables, historical trends, and resource availability reports, equipping network engineers with tools assisting in decision-making for network resource planning.


Here are several screenshots from an interactive tool I developped for network engineers, with the objective of facilitating traffic growth monitoring and capacity planning activities. The menu on top of each page indicates the different dashboards.





### Congestion Table
Another key functionality for this tool is monthly/weekly congestion table. For each circuit ID, it indicates end-routers and interfaces, bandwidth for the logical link, current traffic aggregation (from various statistical perspectives), and predictions from 3 months up to 5 years based on compound 95th percentile and estimated yearly growth. Color codes are used to differentiate between aggregation techniques, but also to highlight links that are already over 80% and also 100% utlization. Filters are added to focus on links from certain regions or links over 70% utlization, but also to modify growth rate if needed. Previous month/week reports are still available in the scroldown menu, although the default is the most recent one. It is possible to select a link and jump into a window showing historical traffic trend for the given link. (Transmission systems and router names are not displayed for privacy purposes.)
![congestion](/assets/congestion.png)

### Failover Table
This dashboard is similar to the previous one under the difference that links are bundled in pairs of primary and secondary paths. So utilization is evaluated for the sum of traffic in both links, simulating the events of failure amd checking whether there is enough failover capacity. Again, one can select a pair of links and display historical trends for their sum of traffic, compared to bandwidth available on each of the links. (Transmission systems and router names are not displayed for privacy purposes.)
![failover](/assets/failover.png)

### Historical Trends
It was mentioned earlier that it is possible to mouse-click on a link, either on logical/geographical map or on congestion and failover tables, to display its historical trend. As shown below, the user can choose to display historical traffic utlization and bandwidth for the previous 24 hours, 7 days, month or year. Below is an example showing traffic trend for a logical link within the past seven days; it is not shown on the screenshot but it is possible to get exact numbers and other valuable information (blured for privacy purposes) upon mouse-overing plots.
![trendW](/assets/trend-id-weekly.png)

Here is another example for the same circuit ID, but this time showing historical trend for the previous year (however, limited to data available... The link under examination was turned up in June only.)
![trendY](/assets/trend-id-year.png)

## Ex 3. Devices & Ports Tracking
I built this type of dashboards to support some operations teams. At every moment it retrieves the number of devices at every hubsite and counts (total vs unused) ports of each type on every device. A port availability report can help to better anticipate shortage of ports and plan for new purchases and power/space requirements, which might be challenging in some hubsites. This report also covers software versions and device models, which is valuable information durig migration and code upgrades. (Hubsites and real counts are not disclosed for privacy purposes.)
![operations](/assets/device-ports.png)
