# Database Engine (DBEngine)

A lightweight, Java-based database management system implementing core database functionality including B+ tree indexing, page-based storage, and SQL-like query operations.

## 🚀 Features

### Core Database Operations
- **Table Management**: Create, modify, and delete tables with flexible schema definitions
- **Data Operations**: Insert, update, delete, and select operations with full CRUD support
- **Indexing**: B+ tree indexing for efficient data retrieval and range queries
- **Page-based Storage**: Efficient memory management with configurable page sizes
- **Metadata Management**: Persistent table and column metadata storage

### Advanced Features
- **B+ Tree Implementation**: Custom B+ tree data structure for fast lookups
- **Configurable Storage**: Adjustable page sizes and storage parameters
- **Serialization**: Persistent data storage using Java serialization
- **Query Optimization**: Efficient query processing with multiple condition support
- **Type Safety**: Support for multiple data types (Integer, String, Double, etc.)

### Query Capabilities
- **Complex Queries**: Support for AND, OR, XOR logical operations
- **Range Queries**: Efficient range-based data retrieval
- **Conditional Operations**: Equal, not equal, less than, greater than comparisons
- **Multi-table Support**: Query across multiple tables and conditions

## 📁 Project Structure

```
dbengine/
├── src/
│   ├── DBApp.java              # Main database application class
│   ├── Table.java              # Table management and metadata
│   ├── Page.java               # Page-based storage implementation
│   ├── Tuple.java              # Data tuple representation
│   ├── bplustree.java          # B+ tree indexing implementation
│   ├── SQLTerm.java            # SQL query term representation
│   ├── DBAppException.java     # Custom exception handling
│   ├── DbappConfig.java        # Configuration management
│   ├── Serializer.java         # Data serialization utilities
│   └── DBAppTest.java          # Test suite
├── bin/                        # Compiled Java classes
├── metadata.csv                # Database metadata storage
└── README.md                   # This file
```

## 🛠️ Installation & Setup

### Prerequisites
- Java Development Kit (JDK) 8 or higher
- Any Java IDE (Eclipse, IntelliJ IDEA, VS Code) or command line

### Quick Start

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd dbengine
   ```

2. **Compile the project**
   ```bash
   javac -d bin src/*.java
   ```

3. **Run the application**
   ```bash
   java -cp bin DBApp
   ```

## 📖 Usage Examples

### Creating a Table
```java
DBApp db = new DBApp();
Hashtable<String, String> columns = new Hashtable<>();
columns.put("id", "java.lang.Integer");
columns.put("name", "java.lang.String");
columns.put("gpa", "java.lang.Double");

db.createTable("Student", "id", columns);
```

### Inserting Data
```java
Hashtable<String, Object> data = new Hashtable<>();
data.put("id", 1);
data.put("name", "John Doe");
data.put("gpa", 3.8);

db.insertIntoTable("Student", data);
```

### Creating an Index
```java
db.createIndex("Student", "gpa", "gpaIndex");
```

### Querying Data
```java
SQLTerm[] terms = new SQLTerm[1];
terms[0] = new SQLTerm();
terms[0]._strTableName = "Student";
terms[0]._strColumnName = "gpa";
terms[0]._strOperator = ">";
terms[0]._objValue = 3.5;

String[] operators = {};
Iterator result = db.selectFromTable(terms, operators);
```

### Updating Data
```java
Hashtable<String, Object> updateData = new Hashtable<>();
updateData.put("gpa", 3.9);

db.updateTable("Student", "1", updateData);
```

### Deleting Data
```java
Hashtable<String, Object> deleteCondition = new Hashtable<>();
deleteCondition.put("id", 1);

db.deleteFromTable("Student", deleteCondition);
```

## 🔧 Configuration

The database engine uses a configuration system that allows you to customize various parameters:

- **MaximumRowsCountinPage**: Maximum number of tuples per page
- **Storage Path**: Database file storage location
- **Index Settings**: B+ tree configuration parameters

Configuration is managed through the `DbappConfig` class and can be modified at runtime.

## 🏗️ Architecture

### Core Components

1. **DBApp**: Main application class handling all database operations
2. **Table**: Manages table metadata and page organization
3. **Page**: Implements page-based storage with configurable capacity
4. **Tuple**: Represents individual data records
5. **B+ Tree**: Provides efficient indexing for fast data retrieval
6. **SQLTerm**: Encapsulates query conditions and operations

### Data Flow

1. **Storage**: Data is stored in pages with configurable sizes
2. **Indexing**: B+ trees provide fast access to data by key values
3. **Querying**: SQL-like queries are processed through condition evaluation
4. **Serialization**: All data is persistently stored using Java serialization

## 🧪 Testing

The project includes a comprehensive test suite in `DBAppTest.java` that demonstrates:

- Table creation and management
- Data insertion and retrieval
- Index creation and usage
- Complex query operations
- Update and delete operations

Run tests using:
```bash
java -cp bin DBAppTest
```

## 📊 Performance Features

- **Efficient Indexing**: B+ tree implementation for O(log n) lookups
- **Page-based Storage**: Configurable page sizes for optimal memory usage
- **Serialization**: Fast data persistence and retrieval
- **Query Optimization**: Efficient condition evaluation and result filtering

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request


## 👥 Authors

- **Database Engine Team** - *Initial work* - [Mark Maged]


- Java Collections Framework for efficient data structures
- Java Serialization API for persistent storage
- B+ Tree algorithm implementation for indexing

## 📞 Support

For questions, issues, or contributions, please open an issue on the GitHub repository.

---

**Note**: This is a lightweight database engine designed for educational and small-scale applications. For production use, consider established database systems like MySQL, PostgreSQL, or MongoDB.
