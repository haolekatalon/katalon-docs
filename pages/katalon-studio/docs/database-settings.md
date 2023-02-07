---
title: "Set up database connection for data-driven testing" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/database-settings.html 
redirect_from:
    - "/display/KD/Database+Settings/"
    - "/display/KD/Database%20Settings/"
    - "/x/tgFO/"
    - "/katalon-studio/docs/database-settings/"
description: 
---

> From Katalon Studio version 8.0.0 onwards, MySQL JDBC driver is removed from Katalon Studio built-in libraries. To continue using it, you can refer to this document: [Implement DDT MySQL](https://docs.katalon.com/katalon-studio/tutorials/how-to-implement-ddt-mysql.html).

This document gives you information on which database can be used for data-driven testing and how to set up the database connection in Katalon Studio.
## Introduce database connection

To do data-driven testing with a database, you can define a database connection that can be used for the whole project and override this global configuration in a test data file later.

To set up a global database connection, go to **Project** > **Settings** > **Database**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/database-settings/KS-DATABASE-Database-settings.png" width=70% alt="Database settings">

Where:

- **Secure User and Password**: select to authenticate the connected database server, disabled by default.
- **User**: The username for authentication in the connected database server.
- **Password**: The password for authentication in the connected database server.
- **JDBC Driver**: The ClassDriverName of the database that has a supported library connection (JDBC).
- **Connection URL**: The connection string of the database server. Katalon Studio supports built-in JDBC Drivers for the following databases:
    - [SQL Server](https://docs.microsoft.com/en-us/sql/connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver?view=sql-server-ver15).
    - [Oracle SQL](https://docs.oracle.com/database/121/JJDBC/urls.htm#JJDBC28268).
    - [PostgreSQL](https://jdbc.postgresql.org/documentation/head/connect.html).

You can set up a connection to one of those three database types with its executable jar file already embedded. Refer to the following table for an availability check:

<table width="100%">
	<tbody>
		<tr>
			<td>
				<p>Built-in Database</p>
			</td>
			<td>
				<p>Version</p>
			</td>
			<td>
				<p>Katalon Studio 7.0.0+</p>
			</td>
			<td>
				<p>Katalon Studio 7.5.0+</p>
			</td>
			<td>
				<p>Katalon Studio Enterprise 7.0.0+</p>
			</td>
			<td>
				<p>Katalon Studio Enterprise 7.5.0+</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>PostgreSQL</p>
			</td>
			<td>
				<p data-pm-slice="1 1 [&quot;bulletList&quot;,null,&quot;listItem&quot;,null,&quot;bulletList&quot;,null,&quot;listItem&quot;,null]">v42.2.17</p>
			</td>
			<td>
				<p>✔</p>
			</td>
			<td>
				<p>✔</p>
			</td>
			<td>
				<p>✔</p>
			</td>
			<td>
				<p>✔</p>
			</td>
		</tr>
		<tr>
			<td>
				<p>Oracle SQL</p>
			</td>
			<td>
				<p data-pm-slice="1 1 [&quot;bulletList&quot;,null,&quot;listItem&quot;,null,&quot;bulletList&quot;,null,&quot;listItem&quot;,null]">v12.1.0.2</p>
			</td>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>
				<p>✔</p>
			</td>
			<td>
				<p>✔</p>
			</td>
		</tr>
		<tr>
			<td>
				<p data-pm-slice="1 1 [&quot;bulletList&quot;,null,&quot;listItem&quot;,null,&quot;bulletList&quot;,null,&quot;listItem&quot;,null]">SQL Server</p>
			</td>
			<td>
				<p data-pm-slice="1 1 [&quot;bulletList&quot;,null,&quot;listItem&quot;,null,&quot;bulletList&quot;,null,&quot;listItem&quot;,null]">v6.2.2</p>
			</td>
			<td>&nbsp;</td>
			<td>&nbsp;</td>
			<td>
				<p>✔</p>
			</td>
			<td>
				<p>✔</p>
			</td>
		</tr>
	</tbody>
</table>

In case you want to use a version other than the version those built-in drivers are compatible with, learn more about [excluding built-in libraries](https://docs.katalon.com/katalon-studio/docs/external-libraries.html#exclude-built-in-libraries).

For those who wish to connect to an external database having a JDBC driver, you need to install its executable jar file accordingly then tell Katalon Studio where to use it for connection. 

## Connect to a database with a built-in driver

The following example illustrates how to connect to a Postgre database that can be used in a whole project.

> Requirements:
> - You have already set up your Postgre database.
> - Postgre database is running.

To establish a connection, go to **Project > Settings > Database**. In **Database**:
   
1. Select **Secure User and Password** to enable **User** and **Password**.
2. Input **User** name and **Password** used for authentication and **Connection URL**.
3. Click **Test Connection** to verify whether your database is connected successfully.
   
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/database-settings/KS-DATABASE-Connect-built-in-library.png" width=70% alt="Connect Database with a built-in driver">

4. Click **Apply and Close** to save your setting.

## Connect to a database with an external JDBC driver

This section demonstrates how to set up the connection to a database with an external JDBC driver.

> Requirements:
> - You have already set up an external JDBC driver.
> - The external JDBC driver is running.
> - An active Katalon Studio Enterprise license.

To start the connection:

1. Download the executable .jar file of the external JDBC driver. For example, we want to connect to the MariaDB Java Client driver. We download the executable .jar file of the MariaDB library from the Maven Repository website here: [MariaDB Java Client](https://mvnrepository.com/artifact/org.mariadb.jdbc/mariadb-java-client).

	> Notes:
	> * From Katalon Studio version 8.2.5 onwards, you can connect with the SAP HANA JDBC driver. Download the executable .jar file of the SAP HANA library in the Maven Repository website here: [SAP HANA JDBC Driver](https://mvnrepository.com/artifact/com.sap.cloud.db.jdbc/ngdbc).

2. Go to **Project** > **Settings** > **Library Management** to **Add** the jar file > click **Apply**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/database-settings/KS-DATABASE-Connect-external-library.png" width=65% alt="Add anexternal JDBC driver">

3. In Project Settings, go to **Database**:

    - Select **Secure User and Password** to enable **User** and **Password**.
    - Input **User** name and **Password** used for authentication and **Connection URL**.
    - Enter **JDBC Driver**.
    - Enter **Connection URL**.
    - Click **Test Connection** to verify whether your database is connected successfully. 

       <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/database-settings/database-mariadb-new.png" width=70% alt="Connect an external JDBC driver">

    - Click **Apply and Close** to complete the connection process.

**Next**: See [Manage Test Data](https://docs.katalon.com/katalon-studio/docs/manage-test-data.html#create-a-database-data).
