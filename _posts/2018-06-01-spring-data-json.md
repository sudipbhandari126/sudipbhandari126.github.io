---
layout: post
title: Working with Spring Data and Json
---
At controller level, spring framework has a provision where it internally handles the representation of domain object into corresponding json using Jackson Library. 



```java
@PutMapping(produces = {"application/json"})
@ResponseBody
public UpdateResponse someMethod(){ 
//do something
return UpdateResponseInstance;
}
```



In the above example whenever the controller gets called someMethod returns an instance of UpdateResponse which is internally converted to it's corresponding json representation. Spring internally uses Jackson API in order to accomplish this task.

However, if we want to get a json representation of our model at places other than controller level we can just go about doing this using Jackson ObjectMapper.

```java
import com.fasterxml.jackson.databind.ObjectMapper;
ObjectMapper mapper = new ObjectMapper();
SomeModelClass someModelObject = someModelRepository.findById(idValue).get();
String modelJson = mapper.writeValueAsString(someModelObject);
```

Likewise, we can convert incoming json string into corresponding domain object using Jackson. Since we need to know what object to map to we need two parameters: json string, domain class.

```java
import com.fasterxml.jackson.databind.ObjectMapper;
DomainObject domainObject = new ObjectMapper().readValue(json, DomainObject.class); 
```

Sometimes, however, we have to deal with json which don't yet have a corresponding class representation. In such cases I personally find Google's gson to be easier to use. For example:

```java
import com.google.gson.JsonObject;
JsonObject inputJson = new JsonParser().parse(requestString).getAsJsonObject();
Set<String> keys = inputJson.keySet(); // this is more useful when class is not modeled yet
```

