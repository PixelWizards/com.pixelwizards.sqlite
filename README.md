com.pixelwizards.sqlite
=========================

[![openupm](https://img.shields.io/npm/v/com.pixelwizards.sqlite?label=openupm&registry_uri=https://package.openupm.com)](https://openupm.com/packages/com.pixelwizards.sqlite/)

Unity Package Manager compatible wrapper for [SQLite](https://www.sqlite.org/index.html) databases.  

This package is a fork of the source repo (https://github.com/rizasif/sqlite-unity-plugin), reorganized into Package Manager structure and published to OpenUPM.

This plugin can be used to access SQLite database for Unity projects. Supports desktop, Android and iOS devices. 

Usage
--------------

### Install via OpenUPM

The package is available on the [openupm registry](https://openupm.com). It's recommended to install it via [openupm-cli](https://github.com/openupm/openupm-cli).

```
openupm add com.pixelwizards.sqlite
```

### Install via git url

Add this to your project manifest.json

```
"com.pixelwizards.sqlite": "https://github.com/PixelWizards/com.pixelwizards.sqlite.git",
```

OpenUPM Support
----------------

This package is also available via the OpenUPM scoped registry: 
https://openupm.com/packages/com.pixelwizards.sqlite

Prerequistes
---------------
* This has been tested for `>= 2018.3`

Quick Start
----------------

Check out https://github.com/sqlitebrowser/sqlitebrowser for an SQLite desktop client / database browser for creating / managing databases

**Getting Started**

1) Import the correct namespaces.

```
using UnityEngine;
using System.Data;
using Mono.Data.Sqlite;
using System.IO;
```

2) Open your database connection; if the database name (My_Database) does not exist it will be created.
```
string connection = "URI=file:" + Application.persistentDataPath + "/" + "My_Database";
IDbConnection dbcon = new SqliteConnection(connection);
dbcon.Open();
```
3) Finally create a query to access your database.
```
IDbCommand dbcmd;
IDataReader reader;

dbcmd = dbcon.CreateCommand();
string q_createTable = 
  "CREATE TABLE IF NOT EXISTS " + "my_table" + " (" +
  "id" + " INTEGER PRIMARY KEY, " +
  "val" + " INTEGER )";
  
dbcmd.CommandText = q_createTable;
reader = dbcmd.ExecuteReader();
```

# Tutorial
Read this [article on medium](https://medium.com/@rizasif92/sqlite-and-unity-how-to-do-it-right-31991712190) for more details on using SQLite with Unity.
