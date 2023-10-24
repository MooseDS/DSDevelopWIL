# Kotlin Util Method

## Json String to Object
- Gson().fromJson() 사용

## Json String to Map
~~~
String jsonString = "{'employee.name':'Bob','employee.salary':10000}";
Gson gson = new Gson();
Map map = gson.fromJson(jsonString, Map.class);
~~~

