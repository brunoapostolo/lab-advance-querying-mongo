![Ironhack Logo](https://i.imgur.com/1QgrNNw.png)

# Answers

### 1. All the companies whose name match 'Babelgum'. Retrieve only their `name` field.

{'name': 'Babelgum'}

### 2. All the companies that have more than 5000 employees. Limit the search to 20 companies and sort them by **number of employees**.

import { MongoClient } from 'mongodb';

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'number_of_employees': {
'$gt': (5000)
}
};
const sort = {
'number_of_employees': -1
};
const limit = 20;

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { sort, limit });
const result = await cursor.toArray();
await client.close();

### 3. All the companies founded between 2000 and 2005, both years included. Retrieve only the `name` and `founded_year` fields.

{
'founded_year': {
'$gte': 2000, 
    '$lte': 2005
}
}

### 4. All the companies that had a Valuation Amount of more than 100.000.000 and have been founded before 2010. Retrieve only the `name` and `ipo` fields.

<!-- Your Code Goes Here -->

### 5. All the companies that have less than 1000 employees and have been founded before 2005. Order them by the number of employees and limit the search to 10 companies.

import { MongoClient } from 'mongodb';

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'number_of_employees': {
'$lt': 1000
  }, 
  'founded_year': {
    '$lt': 2005
}
};
const sort = {
'number_of_employees': -1
};
const limit = 10;

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { sort, limit });
const result = await cursor.toArray();
await client.close();

### 6. All the companies that don't include the `partners` field.

{
'partners': {
'$eq': []
}
}

### 7. All the companies that have a null type of value on the `category_code` field.

{
'category_code': {
'$eq': null
}
}

### 8. All the companies that have at least 100 employees but less than 1000. Retrieve only the `name` and `number of employees` fields.

import { MongoClient } from 'mongodb';

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'number_of_employees': {
'$gte': 100, 
    '$lte': 1000
}
};
const projection = {
'name': 1,
'number_of_employees': 1
};

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { projection });
const result = await cursor.toArray();
await client.close();

### 9. Order all the companies by their IPO price in a descending order.

import { MongoClient } from 'mongodb';

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'ipo.valuation_amount': {
'$gte': 0
}
};
const sort = {
'ipo.valuation_amount': -1
};

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { sort });
const result = await cursor.toArray();
await client.close();

### 10. Retrieve the 10 companies with most employees, order by the `number of employees`

import { MongoClient } from 'mongodb';

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'number_of_employees': {
'$gt': 0
}
};
const sort = {
'number_of_employees': -1
};
const limit = 10;

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { sort, limit });
const result = await cursor.toArray();
await client.close();

### 11. All the companies founded on the second semester of the year. Limit your search to 1000 companies.

import { MongoClient } from 'mongodb';

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'founded_month': {
'$gt': 6
}
};
const limit = 1000;

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { limit });
const result = await cursor.toArray();
await client.close();

### 12. All the companies founded before 2000 that have an acquisition amount of more than 10.000.000

{
'founded_year': {
'$lt': 2000
  }, 
  'acquisition.price_amount': {
    '$gt': 100000
}
}

### 13. All the companies that have been acquired after 2010, order by the acquisition amount, and retrieve only their `name` and `acquisition` field.

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'acquisition.acquired_year': {
'$gt': (2010)
}
};
const projection = {
'acquisition.price_amount': 1,
'name': 1
};

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { projection });
const result = await cursor.toArray();
await client.close();

### 14. Order the companies by their `founded year`, retrieving only their `name` and `founded year`.

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {};
const projection = {
'name': 1,
'founded_year': 1
};
const sort = {
'founded_year': -1
};

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { projection, sort });
const result = await cursor.toArray();
await client.close();

### 15. All the companies that have been founded on the first seven days of the month, including the seventh. Sort them by their `acquisition price` in a descending order. Limit the search to 10 documents.

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'founded_day': {
'$lte': 7
}
};
const sort = {
'acquisition.price_amount': -1
};

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { sort });
const result = await cursor.toArray();
await client.close();

### 16. All the companies on the 'web' `category` that have more than 4000 employees. Sort them by the amount of employees in ascending order.

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'category_code': {
'$eq': 'web'
  }, 
  'number_of_employees': {
    '$gt': 4000
}
};
const sort = {
'number_of_employees': 1
};

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { sort });
const result = await cursor.toArray();
await client.close();

### 17. All the companies whose acquisition amount is more than 10.000.000, and currency is 'EUR'.

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'acquisition.price_amount': {
'$gt': 10000
  }, 
  'funding_rounds.raised_currency_code': {
    '$eq': 'EUR'
}
};

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter);
const result = await cursor.toArray();
await client.close();

### 18. All the companies that have been acquired on the first trimester of the year. Limit the search to 10 companies, and retrieve only their `name` and `acquisition` fields.

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'acquisition.acquired_month': {
'$lte': 3
}
};
const projection = {
'name': 1,
'acquisition': 1
};
const limit = 10;

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter, { projection, limit });
const result = await cursor.toArray();
await client.close();

### 19. All the companies that have been founded between 2000 and 2010, but have not been acquired before 2011.

/\*

- Requires the MongoDB Node.js Driver
- https://mongodb.github.io/node-mongodb-native
  \*/

const filter = {
'founded_year': {
'$gte': 2000, 
    '$lte': 2010
},
'acquisition.acquired_year': {
'$gte': 2011
}
};

const client = await MongoClient.connect(
'mongodb://localhost:27017/',
{ useNewUrlParser: true, useUnifiedTopology: true }
);
const coll = client.db('lab_mongo').collection('lab_mongo');
const cursor = coll.find(filter);
const result = await cursor.toArray();
await client.close();
