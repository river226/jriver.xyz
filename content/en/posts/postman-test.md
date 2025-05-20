+++
date = '2025-05-20T14:41:39-05:00'
draft = false
title = 'Postman API Testing Examples and Guide'
+++

_This is a living Document_

### Check Status
```javascript
pm.test("Status test", function () {
    pm.response.to.have.status(200);
});
```

Alternative Format: `pm.response.to.be.ok;`

### Test for an Empty List
JSON Reponse:
```json
{
    "items":[]
}
```

Test:
```javascript
pm.test("Empty List is returned", function () {
    var response = pm.response.json();
    pm.expect(response.items).to.be.empty;
});
```

### Test for Specific Response
JSON Reponse:
```json
{
    "value": 1
}
```

Test:
```javascript
pm.test("value is 1", function () {
    var response = pm.response.json();
    pm.expect(response.value).to.equal(1);
});
```
_**ALT**_ -   
JSON Reponse:
```json
1
```

Test:
```javascript
pm.test("value is 1", function () {
    var response = pm.response.json();
    pm.expect(response).to.equal(1);
});
```

### Test List Size
JSON Reponse:
```json
{
    "items":[
        // Several Items are returned
    ]
}
```

Test:
```javascript
pm.test("Correct Number of items are returned", function () {
    var items = pm.response.json().items;
    pm.expect(items).lengthOf(6);
});
```

- `>` (Greater Than) - `pm.expect(items.length).to.be.greaterThan(2);`
- `>=` (Greater Than) - `pm.expect(items.length).to.be.greaterThanOrEqual(2);`
- `<` (Greater Than) - `pm.expect(items.length).to.be.lessThan(2);`
- `<=` (Greater Than) - `pm.expect(items.length).to.be.lessThanOrEqual(2);`

Equal Alt - `pm.expect(items.length).to.equal(2);`

### Other Test Cases

- Check Type: `.to.be.an('array')`
- Check Type is not: `.but.not.an('object')` 
- Check for property: `.to.have.property("id")`
- Check for property being missing: `.to.not.have.property("ip")`
- Chain cases: `.to.be.an('array').but.not.an('object')`

### Loop Through a list

```javascript
const items = pm.response.json().items;

pm.test("Validate items through a loop", function() {
    for(let i = 0; i < items.length; i++) {
        var item = items[i];
        pm.expect(item).to.be.an('object');
    }
});
```

### Build Helper Functions

```javascript
helpers = { // Define first to make sure it is inscope later 
  validateListSize:function(list, size) {
    pm.expect(list).lengthOf(size);
  },
  validateList:function(priceInfo) {
    // Several Test cases
  }
};

const items = pm.response.json().items;

pm.test("Validate a large Section", function() {
    helpers.validateListSize(items, 2);
    helpers.validateList(items);
});
```

### Other Tools

**Bruno** - Works the same, but drops the pm part of the test so a status check looks like:
```javascript
test("Status test", function() {
    expect(res.getStatus()).to.equal(200);
});
```

### Resources
[POSTMAN Docs](https://learning.postman.com/docs/tests-and-scripts/tests-and-scripts/)

