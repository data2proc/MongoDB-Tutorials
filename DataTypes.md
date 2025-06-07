## Data Types in MongoDB

In MongoDB, documents are stored in the **BSON** format, which is a binary representation of JSON. Using the BSON format, we can **remotely call procedures**. BSON supports various data types, which we will introduce below:

### 1. String

This data type is one of the **most commonly used** in MongoDB and is used to store **textual data**. The BSON string type is encoded in **UTF-8**. Every string must be a valid UTF-8 sequence.  
![String](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/string.PNG)  

As you can see in the image above, the two fields `fName` and `lName` have the **String** type, and all values are placed within **quotation marks**.

### 2. Integer

This type is used to **store numeric values**. In the image below, the `age` field is of this type.  
![Integer](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Integer.PNG)  

### 3. Double

This data type is used to **store decimal numbers**. For example, in the image below, the **hourly salary** of each employee is stored as a decimal number.  
![Double](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Double.PNG)  

### 4. Boolean

This data type is used to store **true** or **false** values. For example, the **life status** of an employee can be stored using either `true` or `false`.  
![Boolean](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Boolean.PNG)  

### 5. Null

This data type is used to **store a null value**.  
![Null](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/null.PNG)  

### 6. Array

An **array** is a collection of values that can store **data of the same or different types**. In MongoDB, arrays are represented using square brackets `[]`. In the image below, the **employee's skills** are stored in an array format.  
![Array](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Arrays.PNG)  

### 7. Object

This data type is used to store **nested documents**, also known as **Embedded Documents** or **Nested Documents**. Each of these documents can contain other documents within them.  
![Object](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Object.PNG)  

### 8. ObjectId

When a new document is created in a collection, a **unique ID** is automatically assigned to it (if no ID is defined manually). This automatically generated ID is in **hexadecimal format** and is **12 bytes** long, consisting of:

- 4 bytes for the **timestamp**  
- 5 bytes for **random data** (3 bytes for the machine ID, 2 bytes for the process ID)  
- 3 bytes for an **incrementing counter**

You can also create your **own custom unique ID**.

When defining your own ID, you must assign it using the `_id` field. For example, as shown in the image, since `employeeId` is not named `_id`, MongoDB automatically generates a unique ID when the `insertOne` command is executed.

> ⚠️ Note: If you define your own unique ID, the field name **must** be `_id`.  
![ObjectID](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Object_Id.PNG)

### 9. Undefined

This data type is used to **store undefined or unknown values**.  
![Undefined](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Undefined.PNG)  

### 10. Binary Data

This data type is used to **store binary values**, such as **images**, **videos**, **multimedia files**, etc.  
![BinaryData](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Binary%20value.PNG)  

### 11. Date

This data type is used to **store date values**. It can represent dates with **millisecond precision**.

Some commonly used date functions include:

- `Date()`: Returns the **current date** in **string format**.  
  ![Date](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Date.PNG)  
- `new Date()`: Returns the **Date object** as output.  
  ![NewDate](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/newDate.PNG)  
- `new ISODate()`: Similar to the above function, it returns a **Date object** in **ISO 8601 format**.  
  ![ISODate](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/ISODate.PNG)  

### 12. Min & Max Key

The `MinKey` and `MaxKey` types are used to compare a value against the **lowest** and **highest possible BSON element values**, respectively. They are mostly used in **comparison and sorting operations**.

### 13. Symbol

This data type is **similar to String** and is used to store symbolic values. However, it is **not supported by the Mongo shell**, and if encountered, the value will be **automatically converted to a String**.  
![Symbol](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Symbol.PNG)  

### 14. Regular Expression

This data type is used to **store regular expressions**, which are patterns used to match character combinations in strings.  
![RegularExpression](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Reg%20Expression.PNG)  

### 15. JavaScript

This data type is used to **store JavaScript code**.

### 16. JavaScript with Scope

This data type was used to store JavaScript code **along with a scope** (i.e., variables accessible to the code).  
> ⚠️ **Deprecated** as of MongoDB version **4.4**.

### 17. Timestamp

This data type is used to **store timestamp values**. It is particularly useful when you need to **track changes** to a record.  
![Timestamp](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Timestamp.PNG)  

### 18. Decimal

This data type stores **128-bit high-precision floating-point decimal values**.  
It was **introduced in MongoDB version 3.4** and is useful for scenarios where exact precision is required, such as **financial calculations**.  
![Decimal](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Decimal.PNG)  

---

As explained above, **MongoDB**, like other databases, supports **various data types**. Each data type can be used based on the specific **requirements and design** of your application.
