### massive-js
---
https://github.com/dmfay/massive-js

```
npm i massive --save

npm i -g massive
```

```js
const massive = require('massive');
massive({
  host: '127.0.0.1',
  port: 5432,
  database: 'appdb',
  user: 'appuser',
  password: 'appwd'
}).then(db => {...});

db.auth.users.save(
  username: 'alice',
  password: 'supersecure'
).then(alice => {...});

db.auth.users.save({
  id: 1,
  password: 'evenmoresecure'
}).then(alice => {...});

db.tests.insert({
  name: 'application homepage',
  url: 'http://www.example.com',
  user_id: alice.id
}).then(test => {...});

db.auth.users.update({
  'role is': null
}, {
  role: 'default'
}).then(users => {...});

db.tests.findOne(1).then(test => {...});

db.issues.count({test_id: 1}).then(total => {...});

db.issues.find({
  test_id: 1
}, {
  order: [{field: 'created_at', direction: 'desc'}]
}).then(issues => {...});

db.auth.users.save({
  username: 'alice',
  password: 'supersecure'
}).then(alice => {...});

db.auth.users.save({
 id: 1,
 password: 'enenmoresecure'
}).then(alice => {...});

db.tests.insert({
  name: 'application homepage',
  url: 'http://www.example.com',
  user_id: alice.id
}).then(test => {...});

db.auth.users.update({
  'role is': null
}, {
  role: 'default'
}).then(users => {...});

db.tests.findOne(1).then(test => {...});
db.issues.count({test_id: 1}).then(total => {...});
db.issues.find({
  test_id: 1
}, {
  order: [{filed: 'created_at', direction: 'desc'}]
}).then(issues => {...});

db.issues.destroy(3).then(issues => {...});

db.copy_test(test.id, bob.id)
  .then(test => {...})

db.resetTest(test.id).then(tests => {...});

db.test_stats.find({
  url: 'http://www.example.com'
}).then(stats => {...})

db.user_tests.find({}, {
  decompose: {
    pk: 'user_id',
    columngs: {
      user_id: 'id',
      username: 'username'
    },
    tests: {
      pk: 'test_id',
      columns: {
        test_id: 'id',
        name: 'name'
      },
      array: true
    }
  }
}).then(...)

db.saveDoc('test_attributes', {
  productVersion: '1.0.5',
  testEnvironment: 'production',
  web: true,
  accessibilityStandards: ['wcag2a', 'wcag2aa']
}).then(attributes => {...});

db.test_attributes.count({web: true})
  .then(total => {...});
  
db.test_attributes.searchDoc({
  fields : ["testEnvironment", "environment", "applicationnStatus"],
  term : "production"
}).then(matchingDocuments => {...});

db.test_attributes.findDoc(1)
  .then(attibutes => {...});
db.test_attributes.findDoc({web: true})
  .then(matchingDocuments => {...});

attributes.requiresAuthentication = true;
db.test_attributes.saveDoc(attributes)
  .then(attributes => {...});

db.test_attributes.updateDoc(1, {
  requireAuthentication: false
}).then(attibutes => {...});

db.test_attributes.updateDoc({
  web: true
}, {
  browser: 'Chrome'
}).then(changedAttributesDocs => {...});

db.query(
  'update users set password = hash(password) where id < $1 returning *', [3]
).then(users => {...});
```

```js
massive -d appdb
db > db.listTables();
[ 'tests',
  'users' ]
db > db.tests.find({user_id: 1}).then(tests => {...});
```


