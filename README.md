Coverage: 64.4%
# Inventory Management System

This is an application that an end user can interact with via a Command-Line Interface (CLI). The purpose of this application is to manage an Inventory System, where one can apply CRUD (Create, Read, Update, Delete) functionality to Customer, Item, and Order. 

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

1. Fork this project to local Github - This is so you can make endless changes 
2. Clone the repository to your local machine using a Bash of your choice (I used GitBash) 
3. Have Java downloaded 
4. Have Apache Maven Downloaded
5. Ensure Java Development Environemt is installed appropriately 
6. Have a SQL Visual Database Design Tool Installed (I used MySQL Workbench) 
7. When opening project in IDE, Make sure to open as a new 'Maven' project
8. Have knowledge of Databases

### Prerequisites

**Software Required** 

[JDK version 8](https://www.oracle.com/uk/java/technologies/javase/javase-jdk8-downloads.html)

The Java Development Kit (JDK) will allow functionality between Java and Maven. 
*Using a version above 8 will cause issues in this specific project and thus will not compile*


[Apache Maven 3.6.3](https://maven.apache.org/download.cgi?Preferred=ftp://ftp.osuosl.org/pub/apache/)

Apache Maven is a Java Build Tool for Java. This will allow you to run your project. 


[MySQL Workbench](https://www.mysql.com/products/workbench/) 

*This is the unified visual tool for SQL that is used for this project, you may use one of your liking that supports SQL queries* 

MySQL Workbench enables a DBA, developer, or data architect to visually design, model, generate, and manage databases. It includes everything a data modeler needs for creating complex ER models, forward and reverse engineering, and also delivers key features for performing difficult change management and documentation tasks that normally require much time and effort.


[Eclipse IDE](https://www.eclipse.org/downloads/) 

*This is the IDE that is used for this project, you are free to use an IDE of your choice, as long as it supports Maven fucntionality* 

An **integrated development environment** (IDE) is software for building applications that combines common developer tools into a single **graphical user interface** (GUI).


### Installing

A step by step series of examples that tell you how to get a development environment running

**JDK**

To install JDK for your operating system, please refer to the internet for help.


**Apache Maven**

To install Apache Maven, follow the guide in the link provided for the download 


**MySQL Workbench**

To install MySQL Workbench, follow the guide in the link provided for the download 

Once you have everything set up for the databases, you need to create a new server with the name 'ims'. 

```
CREATE SCHEMA IF NOT EXISTS `ims`
```
This will create the database, from here you may create the appropriate tables. 

## Running the tests

You may run the tests in this project. Testing is a crucial part of development because it pinpoints defects in the software and therefore appropriate corrections can be made. 
To run the tests on all the project:
```
1. Under 'Package Explorer` right click on ims project 
2. Hover cursor over 'Coverage As'
3. Click on `2JUnit Test'
```


### Unit Tests 

Unit testing is a way of testing the smallest piece of code that can be logically isolated in a system, for this project, the unit tests are performed on functions or methods. 

In the Project the Unit testing is conducted on the DAO classes. 
```
	@Test
	public void testCreate() {
		final Item created = new Item(2L, "Pencil", 2.99);
		assertEquals(created, DAO.create(created));
	}
```
To run a Unit Test, simply right click in the appropriate class, hover over `Coverage As`, then click on `1 JUnit Test`


### Integration Tests 
Intergration testing is a level of software testing where individual units / components are combined (integrated) and test as a group. The purpose of this level of testing is to expose faults in the interaction between integrated units. 

```
	@Test
	public void testCreate() {
		final String item_name = "Picture Frame";
		final Double item_price = 17.50;
		final Item created = new Item(item_name, item_price);
		
		Mockito.when(utils.getString()).thenReturn(item_name);
		Mockito.when(utils.getDouble()).thenReturn(item_price);
		Mockito.when(itemDAO.create(created)).thenReturn(created);
		
		assertEquals(created, controller.create());
		
		Mockito.verify(utils, Mockito.times(1)).getString();
		Mockito.verify(utils, Mockito.times(1)).getDouble();
		Mockito.verify(itemDAO, Mockito.times(1)).create(created);
	}
```


## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Maven](https://maven.apache.org/) - Dependency Management

## Versioning

We use [SemVer](http://semver.org/) for versioning.

## Authors

* **Chris Perrins** - *Initial work* - [christophperrins](https://github.com/christophperrins)

* **Usama Mahmood** - *Final Delivery* - [UsamaQA](https://github.com/UsamaQA)

## License

This project is licensed under the MIT license - see the [LICENSE.md](LICENSE.md) file for details 

*For help in [Choosing a license](https://choosealicense.com/)*

## Acknowledgments

* **Piers Barber** 
* **Aswene Sivaraj** 
Thank you for putting up with me and jumping on calls. 
