# Case Study: Century Engineering

* **Est.** 1974
* **Offices:** Maryland, Delaware, Pennsylvania, Virginia
* [centuryeng.com][0]

<p style="text-align: center;"><img src="http://fulcrumapp.com/assets/img/cases/ce-logo.png" alt="Century Engineering logo"</p>

Our Asset Management case study focuses around Century Engineering, Inc., a full service engineering consulting firm offering expertise in Civil, Mechanical, Structural, and Geospatial Technology Solutions.

### Program Management Solutions with Fulcrum

Century Engineering, Inc. (Century) is proud to work with the Delaware Department of Transportation Railroad Program ([DelDOT][1]) providing engineering design and technology solutions services related to over 500 railroad crossings that they manage and maintain statewide. DelDOT is responsible for ensuring that all crossings promote safe travel for Delaware citizens, visitors, and railroad operators. This responsibility comes with the task of ensuring all railroad crossing structures are operational and compliant based on Federal and State regulations (ADA and MUTCD). In addition to maintaining the physical assets of the State's railroad crossings, DelDOT also handles public complaints, reported incidents, and coordinates / monitors all construction activities related to maintenance and redesign projects.

![Railroad asset management](http://fulcrumapp.com/assets/img/cases/ce-1.jpg)

### DelDOT Railroad Program Management System

Century has developed an enterprise data solution to allow DelDOT to better manage their assets, as well as improve accessibility to the information that supports their decision-making. Fulcrum enabled the rapid development of a comprehensive data model for the storage of all crossing-related data including: physical crossing assets, recorded incidents, maintenance schedules and construction projects. Multiple teams are able to access this database though the sophisticated Fulcrum iOS and Android apps for the collection of numerous field assets. Through the use of the Fulcrum API Century was able to build a suite of web-based applications to allow DelDOT to see the collected data in real-time.

DelDOT's RPMS leverages several leading technologies that support flexibility and scalability, as the client's needs change over time and through continued use.

* Fulcrum for core database and mobile data capture
* [CartoDB][2] for presentation, and interactivity
* [AngularJS][3] for web application development
* [Bootleaf][4] for map presentation
* [D3.js][5] for data visualization

### Asset Inventory and Inspection

Fulcrum was used to perform a statewide asset inventory/assessment to construct DelDOT's railroad database. Features collected include crossing surface limits, warning devices, rail equipment, signs and striping. The location of each feature was captured along with photo documentation and descriptors about the condition of each asset. Fulcrum streamlines this process by integrating all photo handling natively, eliminating the need to post-process data and providing decision-makers instant access to ground conditions. Since each railroad crossing contains multiple assets, we were able to leverage Fulcrum's [Repeatable][6] data type to support the complex data relationships required. The asset inventory serves as the information core by which all decisions related to maintenance, reconstruction planning, and budgeting are derived.

> "Fulcrum is far more than just a mobile data collection platform."

### Incident Reporting

The Incident Reporting app supports the recording of all railroad-related incidents including auto/pedestrian accidents, citizen complaints, and any reported structure malfunction or failure. The application is structured as a web-based entry tool, supported by the Fulcrum API, which enabled integrated dispatch and incident remediation tracking. Once a new incident is created, the record is highlighted for field review via the Fulcrum status data type. Using the Fulcrum mobile app, field inspectors document the ground conditions, capture photographs, and recommend necessary action steps for remediation. All completed action steps are entered into the incident record. This provides a lineage of remediation steps and supports DelDOT's incident response accountability.

### Construction Monitoring

Century has also assisted DelDOT in the migration from analog (paper/pencil) construction monitoring practices to a fully digital approach with Fulcrum. The Construction Monitoring application provides inspectors with a tool to document all aspects of construction projects from materials, personnel, and equipment quantities to representative signatures and detailed photo documentation. Since railroad construction projects often stretch over multiple days, if not weeks or months, it is important to be able to track progress and quantities to ensure projects are not at risk of falling behind schedule or beyond budget. The collected data is made available, in real-time, via a custom webhook that pushes Fulcrum data to CartoDB, and is presented to office team members through the Construction Monitoring web application. This supports real-time decision-making in the event of unforeseen issues so that potential impacts to construction can be immediately addressed.

![Construction monitoring](http://fulcrumapp.com/assets/img/cases/ce-2.jpg)

### RPMS Summary

To date Century has leveraged Fulcrum to assist DelDOT with the inventory of over 600 public and private, at-grade and grade separated railroad crossings, as well as the detailed tracking of over 30 crossing redesign/reconstruction projects. This includes:

* The collection of over 700 active railroad crossing warning devices
* Capture of over 3,600 railroad-related equipment, striping and warning signs
* Monitoring and documentation of over 1,200 hours of active construction
* Cataloging over 15,000 asset and construction photographs

RPMS provides DelDOT with several benefits including:

* Accountability and transparency through detailed documentation and action reporting
* Centralization of all data used to support the daily operations of the DelDOT Railroad Program
* Real time data delivery allowing project managers to make informed decisions based on current conditions
* Fulfillment of internal and federal reporting requirements (Federal Railroad Administration (FRA))
* Seamless, multi-lateral communication between office and field teams

## Why Fulcrum?

Century chose Fulcrum for many reasons, but primarily for its unmatched mobile data collection capabilities, and the ability to easily integrate with other technologies to provide our clients with comprehensive program management solutions. Additionally Fulcrum provides:

* The ability to centralize data for enterprise consumption and dissemination
* Support for complex data structures characteristic of most field survey tasks
* Adaptability and flexibility to adjust database and mobile interfaces on the fly based on field comments and modifications to data requirements
* A clean and simple mobile app interface that enables us to hide unnecessary data complexities and allows field teams to focus solely on the job of inventory, inspection, and documentation
* Data accessibility made easy through the Fulcrum Dashboard, Data Shares or through custom applications driven by the Fulcrum API and/or webhooks
* Real-time synchronization and information sharing
* Automated handling of voluminous collections of photographs and videos without the extensive post-processing found in legacy workflows
* Support for pairing peripheral Bluetooth GNSS/GPS receivers for high precision location capture on tablets and smart phones
* Multi-team deployment and data conflict resolution

Fulcrum has become a core component of the services provided by Century's Geospatial Technologies (GIS) team. The ability to access Fulcrum from external software/web-based solutions allows us to build enterprise-level tools to fulfill our clients' asset management, mapping, and reporting requirements. We find that industry alternatives are far more expensive while offering far less than what we can achieve with the Fulcrum platform. In 2014, Century leveraged Fulcrum to construct over 30 individual apps comprised of over 30,000 data points and over 40,000 photographs. We look forward to seeing what the Fulcrum Team brings in the future, and we are constantly searching for new ways to use the product for improved data management practices and enhanced decision-making

[0]: http://www.centuryeng.com
[1]: http://www.deldot.gov/
[2]: http://cartodb.com
[3]: https://angularjs.org/
[4]: https://bmcbride.github.io/bootleaf
[5]: http://d3js.org/
[6]: http://fulcrumapp.com/help/repeatable-sections/