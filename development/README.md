# Development

## Know More About Us

* Get to know about the project at [datafibers.com](http://datafibers.com/) \| [datafibers.org](http://datafibers.org/)
* Watch and Star us in [DataFibers Community GitHub](https://github.com/datafibers-community)

  ![](http://i.imgur.com/pvgE3yK.gif)

* Fork and Pull Request when you are ready to contribute
* Contact Us for participant at [datafibers@gmail.com](mailto:datafibers@gmail.com)
* Join our discussion and ask questions at [datafibers@googlegroups.com](mailto:datafibers@googlegroups.com)
* Chat live with us at [DF Gitter](https://gitter.im/datafibers/df?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
* Hear our news and events @ [Facebook](http://www.facebook.com/data.fibers) or [Twitter](http://twitter.com/datafibers1) or Wechat account **DataFibers Community**
* Our Meetup is incoming

## GitHub Repositories

* [df\_data\_service](https://github.com/datafibers-community/df_data_service) - This is core DataFibers services
* [df\_demo](https://github.com/datafibers-community/df_demo) - This is where we build demo for DataFibers and other tookit
* [df\_complete\_guide](https://github.com/datafibers-community/df_complete_guide) - This is the source for this book
* [df\_certified\_connects](https://github.com/datafibers-community/df_certified_connects) - This is where we keep the connects self made or certified for DataFibers
* [df\_web\_admin](https://github.com/datafibers-community/df_web_admin) - This is where we keep the web admin ui
* [df\_api\_doc](https://github.com/datafibers-community/df_api_doc) - This is script for rest api document generator as well as latest document backup
* [df\_doc](https://github.com/datafibers-community/df_doc) - This is where we keep materials for rugular meetup and trainings

## Project Management

DataFibers' issues and kanban borad are two very important tools we are using for DataFibers management and delivery.

* [Issue List](https://github.com/datafibers-community/df_data_service/issues) - This is where we log all backlog items
* [Kanban Board](https://github.com/orgs/datafibers-community/projects/1?fullscreen=true) - This is where we manage and track the progress of work items.

> ![](../.gitbook/assets/tip.jpg) Do not forget to assign the issues under your name once you start working on it.

## How to Contribute

* Fork DF master branch to your own repository.
* Switch to the latest branch.
* Work on the code with your preferred Java IDE.
* Once done, checkin your code changes to your own GitHub repository.
* Create a branch pull request from **your\_github\_repo.development\_YYYYMM** to **df\_github\_repo.development\_YYYYMM**.
* Do proper code merge and changes until you can successfully send the pull request.
* The other DataFibers developers will review, comment, and approve your pull request and merge to **df\_github\_repo.development\_YYYYMM**.
* At the end of every month, release team will merge the monthly development branch to the master having changes from all pulled. All issues related in the [Kanban Board](https://github.com/orgs/datafibers-community/projects/1?fullscreen=true) at _**Done & To Be Merged**_ area will be closed and removed from the Kanban.
* Then, a new branch will be created for the next month as active development branch.

> ![](../.gitbook/assets/information.jpg) When release team merges the pull request, please choose _**create a merge commit**_ in the **Merge pull request** option by clicking the right arrow button and choose as below picture. As result, the code commit and contribution made in the feature branch will be carried over master branch.
>
> ![](https://help.github.com/assets/images/help/pull_requests/select-squash-and-merge-from-drop-down-menu.png)

## How to Debug

There are generally two ways to debug in DF applications

### Server Debug

Server debug is to run server application in debug mode. In this case, we still keep DF dependecy environment, such as Kafka, running inside of VirtualBox, but to run the DF Data Service as server in debug mode outside of VirtualBox.

In order to make this work, we'll need to reforward DF appliation related port, such as 8000 \(for UI\) and 8080 \(for REST Service\) to other port number, such as 8000 to 7000, to make it avaliable for the DF application outside of VirtualBox as follows.

 ![](../.gitbook/assets/debug_port.PNG)  
 Figure 2.1 Forward Port in VirtualBox for Debug

Also, make sure all of the DF dependecy application, such as Kafka, ZooKeeper, have their port forward outside of VirtualBox. Then, we can debug run the entrance function at DFInitService.main\(\).

 ![](../.gitbook/assets/debug_run_idea.png)  
 Figure 2.2 Debug DF DataService in IDEA

### Client Debug

Client side debug is to run client application in debug mode by connecting full DF service in the VirtualBox. All port forwarding should be in place to work in this mode. For features closely related to the DF dependecy application, such as Kafka, ZooKeeper, Flink, etc, you can easily use this mode.

If you meet any exception regarding to connection timeout especially on Kafka or MongoDB, you can refer to the [troubleshooting area](https://github.com/datafibers-community/datafibers-complete-guide/tree/de0445ca4d80e881f015535480562ba3ba4d8169/troubleshooting_area.html#Vagarant_Issues) in this guideline.

> ![](../.gitbook/assets/tip.jpg) The DataFibers application jar set log level to INFO by default. To switch the log level to DEBUG, add -d or --debug as command line option, such as `java -jar target/df-data-service-1.1-SNAPSHOT-fat.jar -d`

