# Design - Group 9

Our project is to create a dynamic scalable instance of Selenium Grid, a framework for testing websites and wep apps in parallel. We are utilizing Microsoft Azure for creating virtual machines to run our Grid's hub and nodes.

The essential objects of our system are The GridManager, the SeleniumScaler, and the SeleniumScraper object classes.

The design of our project consists of a few different parts. We have a SeleniumScaler class that handles the authentication with Azure and the creation/deletion of VMs. On construction, it starts up a VM for our grid hub and a couple VMs that each run 3 nodes with the capability of running up to 5 tests in parallel using Chrome, Firefox, or Edge on each node. 

We have a GridManager class that handles scaling up/down. The GridManager will periodically check our Grid's status and health.

Some information is difficult to get directly from the Grid without injecting a servlet, so we have a SeleniumScraper class that scrapes the HTML from our running Grid and parses it giving us useful information about active sessions and their IDs, which the GridManager will use for deallocation.

The VMs also rely on a set of PowerShell scripts that install necessary packages and set system variables.

One interace for the objects to commuinicate is the ParserPrinter, which gets the information about the specific nodes using the Scraper and communicates to the GridManager/Selenium Scaler classes.

## External Interactions with the System 
![External Interactions](/images/External.png)

## System Architecture for data Collection
![Data Collection](/images/Architecture.png)
