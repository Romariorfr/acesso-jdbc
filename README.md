# Project focused on database access with JDBC

Data persistence is essential in most applications.
The objective of this project is to elaborate a basic structure of a project
with JDBC and also implement the DAO(Data Acess Object) design pattern manually.


one of the main goals is to learn to access the data, making entries,
data recovery, updates and deletions using the JDBC library.


This project implements a data access layer of a small system
that relates all sellers  to their respective departments.

--------

## 1. Methods Features 🎁
### 1.1 method to connect to the database

```Java
public static Connection getConnetion() {
		if (conn == null) {
			try {
				Properties props = loadProperties();
				String url = props.getProperty("dburl");
				conn = DriverManager.getConnection(url, props);
			} catch (SQLException e) {
				throw new DbException(e.getMessage());
			}
		}
		return conn;
	}
```

The _loadProperties_ method is explained below:

```Java
private static Properties loadProperties() {
		try (FileInputStream fs = new FileInputStream("db.properties")) {
			Properties props = new Properties();
			props.load(fs);
			return props;
		} catch (IOException e) {
			throw new DbException(e.getMessage());
		}
	}
```

A file was created in the project root called _db.properties_, containing the database settings. The _loadProperties_ method is responsible for reading this file and returning an object of type Properties that will be passed as a parameter in the getConnection function for connection to the database.

