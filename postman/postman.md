# Postman

## Setting Environment Variable

Put this block of code under "Test"

```
var jsonData = pm.response.json();
pm.environment.set("token", jsonData.token);
```
