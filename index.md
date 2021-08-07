# Content

// Step 1: Scan for a device with 0xffe5 service
navigator.bluetooth.requestDevice({
  filters: [{ services: [humidity] }]
})
  .then(function(device) {
    // Step 2: Connect to it
    return device.gatt.connect();
  })
  .then(function(server) {
    // Step 3: Get the Service
    return server.getPrimaryService(humidity);
  })
  .then(function(service) {
    // Step 4: get the Characteristic
    return service.getCharacteristic(humidity);
  })

   .catch(function(error) {
     // And of course: error handling!
     console.error('Connection failed!', error);
  });
