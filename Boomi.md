
## Integration

* `Process` contains steps that specify the business logic and transformation requirements.
* `Steps` you link together to create the business logic for a process.
* Components` Reusable configuration objects that you use in processes.
* `Runtime` is when a program is running.
* A `runtime engine` powers the program while it is running.
* `Atom Cloud` is the runtime engine you are using in this training.
* `Connector` retrieves data into the integration using one of the application or technology connectors. For many application connectors, the icon is specific to the application.
* `Trading partner` retrieves data into the integration for a specific trading partner and handles common EDI document standards, such as X12 and EDIFACT.
*  `Data Passthrough` retrieves data into the integration from a parent process or another external source.
*  `No Data` The process does not receive data from any source. Instead, a single empty document goes through the process flow.
* You cann't remove it from the process.



#### Connection
* It is suggested to create connection folder and add all connections here and all process use it
* `#` helps to put folders on the top of the list, `z_` put them into bottom

#### Business Scenario I
* The XML files are retrieved from the FTP server, transformed into a comma-delimited flat file with some data modified, and stored in the cloud. 
* FTP server is a service that allows file exchanges between systems over a network

#### Atom
* Create engironemnt and create atom and on environment, you can `Attachment` the Atom you created
* An `Atom Cloud` only integrates with publicly accessible endpoints and  is a single tenant.
* 
