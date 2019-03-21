# graphql_notes

GraphQL Significance
Are you searching for the ideal way to fetch data from multiple sources?
Do you wish to minimize the number of calls to the server?
Do you intend to fetch only the required information other than the additional information?
The answer to the above questions is GraphQL - a query language for APIs.

Today, most of the applications need to get data (stored in a database) from a server. It is the responsibility of the API to implement an interface to the stored data that meets an application needs.

------------------

What is GraphQL?
What is GraphQL?
GraphQL is a query language for APIs and runtime for fulfilling those queries with the existing data. It was developed and open-sourced by Facebook in the year 2015.

Provides a common interface between a client and the server for fetching the data and performing manipulations.
Allows clients to define the required data structure and return the same from the server.
Provides a complete and understandable description of data in API.
----------------------
Example of GraphQL Query
Please find a sample GraphQL query below.

Query


{
DryFruits
{name}
}

Query Response

{
  "data": {
	"DryFruits": [
	 {"name": "Cashew"},
	 {"name": "Badam"}
]
}
}
--------------------
Features of GraphQL
Following are some of the key characteristics of GraphQL.

Hierarchical
Strong-typing
Product-centric
Client-specified queries
Introspective
------------
GraphQL vs REST
Data Fetching: In REST APIs, multiple endpoints are used for gathering an information. Whereas in GraphQL, a single endpoint is used because the data structure is not fixed in GraphQL.

Over/Under fetching: It is easy to fetch more or fewer data with REST. But in GraphQL, only the required information is fetched from the server.

Versioning: Unlike REST APIs, versioning is not required in GraphQL since we can easily add new fields and types to GraphQL API without impacting the existing data.
---------------
REST vs GraphQL Queries
Imagine you want to request an information from a post entity and at the same time you also want to request an information of post user. Let's see how these are queried using REST and GraphQL.

REST Query

mydomain.com/users/:id
You require two end points in REST, one for retrieving post entity and the other for retrieving the information of post user. The same information can be retrieved in single query using GraphQL. The query is shown below.

GraphQL Query

{
     post(id: 1) {
        title
        user {
            name
            email
            courses {
                title
            }
        }
     }
}

---------------
GraphQL - Clientbase
GraphQL - Clientbase
Following are some of the clients using GraphQL.

Facebook
Coursera
GitHub
Twitter
Shopify
PayPal
-------------
GraphQL - Architecture
GraphQL is a specification that defines the GraphQL server behavior. It is a set of guidelines on how the requests and the responses should be handled.

The following are the three different kinds of architectures that contain a GraphQL server.

GraphQL server with a connected database.
GraphQL server that integrates the existing system.
Hybrid approach (combination of the above two architectures).
-----------------------------
GraphQL Server with a Connected Database
GraphQL Server with a Connected Database
This architecture contains the database and GraphQL server integrated on a single node.

The database can be SQL, MongoDB, and even a REST API connected to a database.

The desktop/mobile (client) communicates over the GraphQL server over HTTP.
The server reads the request payload, process the request, fetches the data and return the data to the client.
---------------------------
GraphQL Server that Integrates Existing System
GraphQL Server that Integrates Existing System
GraphQL is used to combine legacy infrastructure, third-party APIs and microservices in the existing system.

In this architecture, GraphQL acts as an interface between the client and the existing systems.

Client applications communicate with the GraphQL server that resolves the query.
The above approach is useful for the firms that have the legacy infrastructure and distinct APIs.
-------------
Hybrid Approach
Hybrid Approach
The hybrid approach is the combination of the previous two architectures. In this approach, GraphQL server will resolve any received request.

Data is received either from the database or from the integrated APIs.
----------------------------
GraphQL Installation
Requirements

Terminal
npm needs to be installed.
Code editor (Visual Studio code - recommended)
-------
GraphQL Extension
Visual Studio Code is provided with some extensions. These extensions will make your experience as a developer smoother working with GraphQL.

GraphQL for VSCode is one of the extensions available for GraphQL in Visual Studio code.

Select the extension from Visual Studio code editor and click the Install option to install it.
---------------------
Introduction to GraphQL Schema
A GraphQL schema is at the center of any GraphQL server implementation and explains the functionality available to the clients that connect to it.

The core building block within a schema is the "type" that provides a wide range of functionality within a schema. It can

Create relationships between types (e.g., between a Book and an Author).
Define data-fetching and data-manipulation operations to be executed by the client.
Self-explain the capabilities available to the client (via introspection).
------------
Root Types in Schema
The following are some of the special root types present for writing the schema for an API.

type Query{ ...}

type Mutation{ ... }

type Subscription{ ...}

Query, Mutation, and subscription are entry points for the requests sent by the client.
------------------
Schema Definition Language(SDL)
GraphQL has its own system type which is used to define the API schema. The schema syntax is written using a language known as Schema Definition Language(SDL).

The following is an example showing how to use SDL in defining a simple type Product.

 type Product {
  name: String!
  manufacturingDate: Int!
}
The above example has the Product object followed by two fields namely name and manufacturing date of type String and Int. The ! following the type means that the field is mandatory and non nullable.
-------------
Schema Types
Schema types define the GraphQL server capabilities and allows the GraphQL operations to be validated.

Scalar types : Represents the operation leaves and always resolves to concrete data.

Object types : Represents the group of fields

Query type : They define the entry point into the server for fetching data.

Mutation type : Defines the entry point into the server for modifying server data.
-------------
Introspection
GraphQL has a great feature of querying its own schema that allows you to view the query and mutation details available in your schema. It also gives the details regarding the argument they accept and even the available fields for querying.

The following example queries all the fields present in your schema.

Example

{
  __schema {
    queryType {
      name
      fields {
        name
        description
        type {
          name
          description
        }
      }
    }
  }
}
------------
Introduction to GraphQL Query
GraphQL Queries allows you to ask the server for the required data. They also give the full power for the client to ask for the exact information.

GraphQL API's are usually exposed to a single endpoint because the data structure that is returned is not fixed rather it is flexible.

Query Syntax 1:

query query_name{
someField
}

Query syntax 2:

{
someField
}
-----------------
Objects and Fields
Object is a type with some fields. A field is termed as the data.

Example

Query

{
  fruit {name}
}
Response

{
  "data": {
   "fruit": {"name": "Mango"}
 }
}
In the above example, fruit is an object and name is the field within an object.
-----------------
Basic Query
This query returns all the objects of a type.

Example:

{
category{name}
}
The above query returns all the category names as shown below.

{
  "data": {
    "category": [
      {"name": "Physics"},
      { "name": "Maths"}
    ]
  }
}
-------------------
Searching with Arguments
Fields take the arguments as input. Arguments can be used to determine the return value. They help us to retrieve the specific information from the server.

Example

{
  human(id: "1500") {
    name
  }
}
The above query returns only the name of the human with an id 1500.

{
  "data": {
    "human": [
      { "name": "Tom"}
    ]
  }
}

--------------
Multiple Arguments
Besides ids, you can give additional arguments to the query methods. These methods return only those objects that have in their fields values corresponding to the values of those arguments. You can also pass multiple arguments to the objects as shown below.

Example

{
  fruits(color:  "red", size: "medium" ) {
    name
  }
}

The above query returns all fruits with red color and medium size.

{
  "data": {
    "fruits": [
      {
        "name": "apple"
      }
    ]
  }
}

--------------
Searching by subfields
The fields of an object can itself be an Object with its own fields. You need to mention the fields and the subfields to be returned, in the query. You need to make the selection for the subfields in a field for the query to work.

Example

{
  products(id: "7") {
    name
    price
    category {   name}
    vendor {name}
  }
}

The above query renders the following output.

{
  "data": {
    "products": [
      {
        "name": "watermelon",
        "price": 25,
        "category": {
          "name": "Fruits"
        },
        "vendor": {
          "name": "Fresh Fruits"
        }
      }
    ]
  }
}
--------------

Aliases
Querying directly for the same field with different arguments is not permitted in GraphQL, because that would result in an error. Aliases remove these conflicts and give the required output. Aliases permits us to provide the field a customized name and to request data from the same fields with various arguments

Example

query getUsers
{
admins: users(role:"admin")
{
id
first name
last name
}
accountants: users(role:"accountant")
{
id
first name
last name
}
}
admins and accountants are the aliases in the above example.
-------------------
Mutation Example
The syntactical structure of mutations is same as queries, but the only difference is that mutations start with the keyword mutation.

Example

mutation {
  createProduct(name: "Samsung", color: black) {
    name
    color
  }
}
-----------------------
Adding Mutations
New objects of the main types can be added with the corresponding add mutations. To do this, you need to provide all attributes for the object.

mutation {
  addCategory(id: 6, name: "Fresh Fruits", vendor: [6, 3, 1]) {
    name
    vendor {
      name
    }
  }
}
-------------------
Updating Mutations
You can change an object of a specified type by providing id. You have an option to change all attributes or only a few depending on the attributes that you provide.

The following example shows how to update an existing data that is stored in the back-end.

Example

mutation {
  updateCategory(id: 2, name: "Fresh Fruits", products: [8]) {
    name
    products {
      name
    }
  }
}
---------------
Deleting Mutations
You can delete an object by providing its id.

The following example deletes an object with id 1.

Example

mutation {
  deleteCategory(id: 1) {
    name
}
-------------
Subscriptions
GraphQL offers subscriptions to have a real-time connection to the server so that the important events get informed immediately. This is one of the most important requirements for today's applications.

When a client subscribes to an event, it will initiate and hold a stable connection to the server. Whenever the particular event happens, the server pushes the corresponding data to the client.
-------------
Subscription Example
The syntactical structure of subscription is same as the queries and mutations.

Here is an example where the event happening on the type product is subscribed.

Example

subscription {
  newProduct {
    name
    color
  }
}
------------------
Real-Time Applications of GraphQL
GitHub chose GraphQL for API v4 because it offers significantly more flexibility to their integrators.

GraphQL has powered Facebook mobile apps since 2012.

Coursera have built tooling to dynamically translate their REST APIs to GraphQL, by allowing the backend developers to continue writing the APIs they are familiar with and parallelly giving the full access to the whole data to the client developers using GraphQL.
----------------------------
