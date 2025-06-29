# Geospatial Concepts in MongoDB

Working with coordinates and location-based data can often be complex and challenging. In this article, we explore how to store geospatial data, create geospatial indexes, and use relevant methods provided by MongoDB.

MongoDB offers functionality for storing geographic points in the `geoJSON` format. A geographic point is defined by two values: **longitude** and **latitude**.

- **Longitude** must be a number between `-180` and `180`
- **Latitude** must be a number between `-90` and `90`

Before diving deeper, let’s briefly introduce the `geoJSON` format and the types of geospatial data it supports. `geoJSON` is a format for encoding a variety of geographic data structures. It is based on the JSON format and supports the following geometry types:

- `Point`
- `LineString`
- `Polygon`
- `MultiPoint`
- `MultiLineString`
- `MultiPolygon`
- `GeometryCollection`

## Point

Represents a single geographic point. The structure is as follows:

```json
{ "type": "Point", "coordinates": [30, 55] }
```
## LineString  

Represents a path using an array of two or more points. The structure looks like this:  
```json
{ "type": "LineString", "coordinates": [[27, 67], [52, 4]] }  
```
## Polygon
A polygon is a closed shape defined by a series of lines (minimum of 4 coordinates), where the first and last points must be the same.  
```json
{
  "type": "Polygon",
  "coordinates": [[[2, 1], [3, 4], [5, 1], [2, 1]]]
}
```
## Nested Polygons (with holes)
You can also define nested coordinates (e.g., a polygon with a hole):  
```json
{
  "type": "Polygon",
  "coordinates": [
    [[0.01, 0.02], [7.01, 1.03], [3.01, 5.1], [0.01, 0.02]],
    [[2.0, 1.01], [4.0, 2.0], [3.02, 3.0], [2.0, 1.01]]
  ]
}
```
The visual representation of such a structure would show a polygon with an inner excluded region.  

![polygon](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Polygons.png)  

## MultiPoint

If a `LineString`-like structure contains an array with more than two coordinate points, it is referred to as a `MultiPoint`.

```json
{
  "type": "MultiPoint",
  "coordinates": [
    [162.07985, 20.66911],
    [126.73567, -21.59424],
    [-57.94873, 0.03998]
  ]
}
```
## MultiLineString
A MultiLineString is similar to a LineString, but it contains an array of multiple lines.  
```json
{
  "type": "MultiLineString",
  "coordinates": [
    [[162.07985, 20.66911], [163.07945, 21.56721]],
    [[126.73567, -21.59424], [127.74537, -22.54623]],
    [[-57.94873, 0.03998], [-58.73823, 1.12934]]
  ]
}
```
## MultiPolygon
This is similar to the Polygon type, but it stores an array of multiple polygon shapes.  
```json
{
  "type": "MultiPolygon",
  "coordinates": [
    [[[0.01, 0.02], [7.01, 1.03], [3.01, 5.1], [0.01, 0.02]]],
    [[[2.2, 1.01], [4.02, 2.01], [3.2, 3], [2.2, 1.01]]]
  ]
}
```
## GeometryCollection
This is one of the more complex geoJSON types. It allows you to group different geometry types—such as MultiPoint, MultiLineString, and MultiPolygon—into a single object.  
```json
{
  "type": "GeometryCollection",
  "geometries": [
    {
      "type": "MultiPoint",
      "coordinates": [
        [162.07985, 20.66911],
        [126.73567, -21.59424],
        [-57.94873, 0.03998]
      ]
    },
    {
      "type": "MultiLineString",
      "coordinates": [
        [[162.07985, 20.66911], [163.07945, 21.56721]],
        [[126.73567, -21.59424], [127.74537, -22.54623]],
        [[-57.94873, 0.03998], [-58.73823, 1.12934]]
      ]
    },
    {
      "type": "MultiPolygon",
      "coordinates": [
        [[[0.01, 0.02], [7.01, 1.03], [3.01, 5.1], [0.01, 0.02]]],
        [[[2.0, 1.01], [4.0, 2.0], [3.02, 3.0], [2.0, 1.01]]]
      ]
    }
  ]
}
```  
## Types of Indexes for Geospatial Data
## 1. 2D Index
A 2D index is used when performing calculations on a two-dimensional Euclidean plane.

Syntax: 
```javascript
db.<collection>.createIndex({ <location_field>: "2d" })
```
Example:

Let’s insert some user-related data into a collection:  
```javascript
db.users.insertMany([
  { name: "Alice", location: [30, 55] },
  { name: "Bob", location: [32, 53] }
])
```
Next, we create a 2D index:  
```javascript
db.users.createIndex({ location: "2d" })
```
To clarify the concept, consider the following example:  
In the first step, we insert user-related data into the collection as shown below.  
![Contact](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/insertContact.PNG)  

In the next step, we create a 2D index on the `address` field:

```javascript
db.contacts.createIndex({ address: "2d" })
```
![Index](https://github.com/data2proc/MongoDB-Tutorials/blob/main/images/Index2d.PNG)  

![Here](https://github.com/data2proc/MongoDB-Tutorials/blob/main/CRUD.md), we will provide a brief explanation of how to write queries and use common methods that operate on this type of geospatial data.  

## 2. 2dsphere Index

The **2dsphere** index is used when you need to perform calculations or queries on spherical (Earth-like) geospatial data. If your data revolves around the poles or spans long spherical distances, the 2D index is not suitable. Instead, you should use the 2dsphere index.

**Syntax:**

```javascript
db.<collection>.createIndex({ <location_field>: "2dsphere" })
```
For more detailed information about geospatial methods and queries, refer to the official MongoDB documentation:  
![Documentation](https://www.mongodb.com/docs/manual/geospatial-queries/)  



