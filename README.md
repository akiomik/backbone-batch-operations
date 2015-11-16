backbone-batch-operations
--------------------------
This is a backbone.js plugin provides batch operations.

## Installation

Install with Bower:

```bash
bower install backbone-batch-operations
```

Add following line to your html.

```html
<script src="javascripts/backbone-batch-operations.js" type="text/javascript"></script>
```

## Sample

```javascript
var Document = Backbone.Model.extend({});
var Documents = Backbone.BatchCollection.extend({
    model: Document,
    url: 'http://example.com'
});
var docs = new Documents({});

// Insert
var models = [
    {'some': 'data'}
];
docs.add(models, {silent: true});
docs.save();    // POST

// Update
docs.each(function(doc) {
    var json = doc.toJSON();
    json.some = 'data was modified';
    doc.set(json, {silent: true});
});
docs.save(); // PUT

// Delete
var models = docs.models;
docs.remove(models, {silent: true});
docs.save();    // PUT
```

## Reference
### collection.save([options]);

### collection.isNew();

### collection.isChanged();

## License
The MIT License. See `LICENSE` file.
