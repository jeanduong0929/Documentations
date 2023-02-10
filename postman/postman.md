# Postman

## Setting Environment Variable From Json Reponse

Put this block of code under "Test"

```
var jsonData = pm.response.json();
pm.environment.set("token", jsonData.token);
```
