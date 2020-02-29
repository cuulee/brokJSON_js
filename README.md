# BrokJSON
Ever struggled with huge GeoJSON-Files? BrokJSON is your space-saving alternative! Depending on your data you can save up to 80%. **Withouth losing any data!** Why? Because it is based on the same ideas as GeoJSON but reduces redundancies.
  
The idea behind BrokJSON: **RAM is mightier than the bandwidth** - download the small BrokJSON and convert it on runtime to GeoJSON than loading a huge GeoJSON.  

Have a look at https://www.brokjson.dev!

## Example
This **GeoJSON** with just two Points...
```json
{
  "type": "FeatureCollection",
  "features": [
  {
    "type": "Feature",
    "properties": {
      "id": 1,
      "title": "Datapoint 1",
      "value": 343
    },
    "geometry": {
      "type": "Point",
      "coordinates": [8.5402,47.3782]
    }
  },
  {
    "type": "Feature",
    "properties": {
      "id": 1,
      "title": "Datapoint 2",
      "value": 14
    },
    "geometry": {
      "type": "Point",
      "coordinates": [8.5637,47.4504]
    }
  }]
}
```
... looks as a **BrokJSON** like this:

```json
{
  "properties": ["id", "title", "value"],
  "geometries": [{
    "type": "Point",
    "features": [
      [[8.5402, 47.3782], [1, "Datapoint 1", 343]],
      [[8.5637, 47.4504], [1, "Datapoint 2", 14]]
    ]
  }
]}
```
No information lost, everything is there. Amazing!


## Installation
### Install via NPM
```console
npm install brokjson
```

### Install standalone
Download `build/brokjson.min.js`  
Add it to your Website
```html
<script src='brokjson.min.js'></script>
```

## Usage
### Node
```js
// Include BrokJSON
brok = require('brokjson')

// Load your GeoJSON
var geojson = {
  "type": "FeatureCollection",
  "features": [
  {
    "type": "Feature",
    "geometry": {
      "type": "Point",
      "coordinates": [8.5402,47.3782]
    }
  }]
}

// Convert your Json-Object to BrokJson
const brokjson = brok.geo2brok(geojson);

// "brokjson" is your BrokJSON as a javascript object
console.log(brokjson)

// Convert it back
geojson = brok.brok2geo(brokjson)
console.log(geojson)
```

### JavaScript
```html
<script src='brokjson.min.js'></script>
<script>
  // Load your GeoJSON
  var geojson = {
    "type": "FeatureCollection",
    "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [8.5402,47.3782]
      }
    }]
  }

  // Convert your Json-Object to BrokJson
  const brokjson = brok.geo2brok(geojson);

  // "brokjson" is your BrokJSON as a javascript object
  console.log(brokjson)

  // Convert it back
  geojson = brok.brok2geo(brokjson)
  console.log(geojson)
</script>

```

## Documentation
BrokJSON is a lightweight library, there are only two functions.
### GeoJSON to BrokJSON
```js
geo2brok(geoJsonObject)
```
**Parameters**  
`GeoJSON` as a `Javascript-Object`

**Return value**  
`BrokJSON` as a `Javascript-Object`

### BrokJSON to GeoJSON
```js
brok2geo(brokJsonObject)
```
**Parameters**  
`BrokJSON` as a `Javascript-Object`

**Return value**  
`GeoJSON` as a `Javascript-Object`

## Full Spec and other languages
Have a look at https://www.brokjson.dev