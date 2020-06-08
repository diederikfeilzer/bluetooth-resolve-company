# bluetooth-resolve-company

## Instalation

```
npm install bluetooth-resolve-company
```

## Usage example with the noble package

```js
var noble = require("noble");
var manufacturers = require("bluetooth-resolve-company");

noble.on('stateChange', function (state) {
  if (state === 'poweredOn') {
    noble.startScanning([], true);
  } else {
    noble.stopScanning();
  }
});

noble.on('discover', function(peripheral){ 
  var manufacturerData = peripheral.advertisement.manufacturerData;
  if(manufacturerData) {
    console.log('Found a BLE device created by: ' + manufacturers.resolve(manufacturerData));
  }
});

```
